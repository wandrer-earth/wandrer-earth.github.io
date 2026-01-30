---
layout: post
title:  "The evolution of Wandrer's 'untraveled roads' feature"
date:   2026-01-30
author: Craig
tags:  tech
cover: "/assets/images/2026-01-30-wandrer-untraveled-roads/traveled-untraveled-header.png"
---

*(A version of this post also appears on the Strava Community Hub)*

Wandrer is the game you win by exploring new places. The main rule is that you get credit for every road you travel, but only once. In order to progress, you have to go places you've never been before.

You can connect your Strava account to Wandrer [right now](https://wandrer.earth) for free and see how much of your town/city/country/continent you've completed. We've only had one country completion so far ([Singapore](https://news.wandrer.earth/2024/05/24/completing-an-entire-country.html)), but maybe you can be the next one to do so (especially if you live in Monaco, Andorra, Liechtenstein, or San Marino).

The core functionality of Wandrer is crediting the user with the sections of road that they've completed. Determining these numbers of a subject of a separate post, but for now let's just go with the concept that all of the GPS data from your activities gets boiled down to "completed portions of roads": 0-100% of Main Street, 25-72% of Spring Street, etc.

In order to know what portions have been completed, Wandrer must also keep track of the portions of a road that the user hasn't completed. At a basic level, these just inverses of each other. If you've traveled 0-40% of a road, then the untraveled portion is 41-100%. Or if you haven't traveled on a road at all, then the untraveled portion is simply 0-100%.

![](/assets/images/2026-01-30-wandrer-untraveled-roads/traveled-untraveled.png){:style="width: 100%; display:block; margin-left:auto; margin-right:auto"}
<figcaption>Side-by-side image of your GPS data (red) with traveled road credited in blue. Untraveled roads are shown on the right in black.
</figcaption>

This is all background to the real subject of this post, however, which is more of a case study in how Wandrer displays information about your incomplete and untraveled roads. As you have seen, nothing about that road information is terribly hard to understand, but how the untraveled roads feature has been implemented has taken several different forms as Wandrer has grown.

This seemed like a good feature to discuss because, while the ability to view your untraveled roads is an important part of Wandrer, I think most folks would consider it a small aspect of the site overall and might not be aware of the work involved in designing and re-designing it. Each incremental improvement led to another, so much so that the current implementation of the untraveled roads feature is pretty unrecognizable from the first version.

# The early days

In the beginning, Wandrer only worked for bicycle rides and only in the Atlanta, Georgia area. Viewing the map of your progress on Wandrer showed only what roads you had completed and nothing else.

On its backend, Wandrer had a single PostgreSQL + PostGIS database, with standard tables for user data and preferences. The database also had a reference table of OpenStreetMap road geometries and a separate "segments" table. The segments table stored the sections of road that the user had completed, with each row being essentially `user_id, osm_id, completed_ranges, geometry`. PostGIS's `ST_LineSubstring()` function was used with the OpenStreetMap road geometry and the `completed_ranges` column to generate the traveled-portion geometry that was displayed on the map.

This is the most straightforward and naive implementation of displaying features on a map: just store each feature in a database and grab them when the user views their map, all served as a big GeoJSON blob. GeoJSON is a JSON-compatible format for sharing geometry data. It has some drawbacks that we'll get into, but Mapbox GL (Wandrer's mapping library) is able to display it natively. This was fine as a starting solution, but we'd soon run in to problems.

# Seeing the world

As Wandrer grew to cover the entire planet, two things happened. The first is that big Strava users started to show up. In Atlanta, the user with the most Strava activities had around 1500 total activities. After expanding to the whole world, Wandrer was dealing with some users having over 9000 activities. The method of "send a GeoJSON blob of everything" for displaying a user's map would not scale to this level of activity at all; you'd have to download 20 megabytes of data each time you loaded the map, and then face the additional delay of your computer processing and rendering that data.

The second thing that happened was that the question of "what counts as a road?" came up more frequently, and the answer to this question is somewhat philosophical and varies substantially by country and user preference. Different classes of roads could be legally accessible or not, some users wanted to ride alleyways, some users didn't want to ride mountain bike trails, etc.

Folks in the Strava Wandrer forum wanted to see which roads counted, at the very least so as to not waste time biking down streets that weren't in Wandrer's dataset. This meant adding an additional "untraveled" data layer to user progress map, adding `missing_ranges` and `missing_geometry` columns to our segments table, and calculating those geometries and ranges with each activity.

But it also meant Wandrer had a bigger problem to address. As of December 9, 2025, planet Earth has [76 million kilometers](https://wandrer.earth/a/earth) of bikable roads. Even for the most dedicated of cyclists, 99% of roads on the planet will be "untraveled." Sending over a big GeoJSON blob of a user's traveled roads was fast becoming untenable, but sending over a GeoJSON blob of all of their untraveled roads would be completely impossible.

Among other things, the first thing Wandrer needed was some kind of spatial index, where the database could locate and send only the geometry features relevant to what the user was actually viewing.

## Aside: web mapping formats

One of the issues that Wandrer was encountering at this point is that, while GeoJSON is a format for sharing geometry data, it's not great for web maps. While there are many formats for spatial data out there (Shapefile, KML, geobuf, etc), a format like Mapbox Vector Tiles (MVT) is a big improvement over GeoJSON for web maps because it has 4 important features:

1. A built-in indexing system. This lets you request only the features contained in a specific area without needing to download the entire dataset. This would be possible to do with GeoJSON and PostGIS, but has to be built by hand.

2. An understanding of zoom levels. When generating a "zoom 1" vector tile (zoomed out far enough to see a quarter of the planet) you can merge, simplify, or remove features that would show in full detail at "zoom 11" (zoomed in close enough to see major streets).

3. A compact binary format. Vector tile data is based off of Google Protocol Buffers and can represent geometries much more efficiently than the text-based GeoJSON. This means faster download and rendering times.

4. A simple storage system. Vector tiles can be stored in a SQLite database file. You can put vector tile data on a cheap VPS and be serving map data within minutes. Wandrer has an open-source [nginx extension](https://github.com/durkie/ngx_http_mbtiles_module) for doing this.

In the years since Wandrer started, there has been a bit of a renaissance in geospatial and web mapping technologies, with things like [PMTiles](https://docs.protomaps.com/pmtiles/), [GeoParquet](https://geoparquet.org/), [DuckDB](https://duckdb.org/) enabling all kinds of new applications for spatial analysis and mapping. It's a good time to be playing with maps.

# Wandrer's transition to vector tiles

PostGIS has built-in functions for generating vector tile data, so Wandrer was quickly able to serve vector tile data instead of GeoJSON. And just as quickly, Wandrer ran in to a new problem: generating vector tile data uses a lot of CPU. This was slamming the database trying to serve vector data on-demand, and still had delays of several seconds before the data was available.

I tried to pre-calculate tiles in the background, storing the result, and serving it when requested. This ultimately was impossible to keep up with and flawed in its approach since it didn't really address the root problem; all of the background jobs were still fetching vector tile data from the (overwhelmed) database.

It was at this point that I discovered the excellent [tippecanoe](https://github.com/felt/tippecanoe) vector tile processing software. GeoJSON in, vector tiles out. Not only is tippecanoe super fast, it also allowed me to work around the database-CPU bottleneck. I could now pull geometry data down to a separate server and do CPU-intensive tile processing there. If that became slow, I could spin up more servers to handle the load faster and cheaper than spinning up and synchronizing new database replicas.

It essentially turned our CPU-bound database problem into an IO-bound problem. Fortunately, databases tend to be very good at IO, and there are tricks we can employ to reduce the load if needed, like caching or processing only the tiles that have changed.

It also turned our tile rendering problem from a synchronous one (map data generated and served on demand) to an asynchronous one (map data generated on our own schedule). We could create vector tile files on a powerful server in the background and then put the files on a cheap VPS, totally separate from the main Wandrer app. Up until recently, Wandrer served almost 400,000 separate vector tile archives this way on a $10/month server.

# Further simplification

With these changes, the "segments" table became superfluous: it had grown to over 100GB, and almost all of that was storage of traveled and untraveled road geometries. Since we no longer needed to render features on demand, rows in this table could be simplified down to just an OSM way ID and ranges for the completed portions. Storing the ranges for the untraveled portions is unnecessary since it's just the inverse of the completed ranges.

And so we're left with only needing the aggregated `(osm_id, ranges)` data for a user, which is just the output of processing their activities. This means the separate "segments" table was not serving any purpose anymore. We could instead send a SQLite export of all of the user's activity data and OSM geometries to our separate tile processing server and let it handle the aggregation and geometry operations before passing the data on to tippecanoe.

![](/assets/images/2026-01-30-wandrer-untraveled-roads/offload.png){:style="width: 100%; display:block; margin-left:auto; margin-right:auto"}

And this is exactly how Wandrer does it today: a cheap, high-CPU core server from Hetzner that processes tile data and sends the result over to a basic VPS. The VPS has no reliance on any other part of Wandrer and basically never has any issues serving requests.

# What about the untraveled roads?

Right! So all of this was laying the groundwork for being able to render a user's untraveled roads. Now that we're able to efficiently request a user's traveled road data for a given tile, Wandrer's current approach is:

1. The backend receives a request for a particular tile of untraveled map data.

2. It, in turn, fetches the user's traveled data (from the VPS) for that tile.

3. It also fetches the raw OSM geometries for that tile data.

4. It subtracts the "traveled data" in step 2 from the "total data" in step 3, leaving just the untraveled portion.

5. It encodes and serves the result.

This is all done on demand and, yes, is slower than serving a user's traveled roads data. There's three factors here that make it work:

1. Tile processing is off-loaded to the separate high-CPU core server, keeping the main app responsive.

2. Untraveled roads are only visible at zooms 11 and up. This limits the number of features that potentially have to be rendered.

3. A 5-minute cache. Long enough to serve an already-calculated result, short enough to avoid being stale.

This could totally work with an asynchronous approach as with the traveled map data. It's just been fast enough so far that that hasn't been necessary.

# Final thoughts

What I like about the evolution of this feature is that it has some very common software architecture themes in it, like, "how do you reframe one big problem into many small problems?" We no longer need to care about how many activities a user has since we can serve only the portions of the map in view, rather than the entire dataset.

Another theme that comes to mind is, "what can be done in the background and what has to be done live?" Wandrer still uses both approaches for serving map data, and it feels like the right balance. Moving expensive computations out of the main app database and on to an external tile-processing server was absolutely the right choice. As Wandrer grows or requirements change, it's possible that I'll need to rethink this feature once again.

And finally, the question of "what does it make sense to scale?" comes up. Just scaling up the app's main database server was always an option here, but adding CPU to a hosted Postgresql database comes at a much higher price than a correspondingly powerful VPS. Being able to offload common data processing tasks to an external "dumb" server is way cheaper and frees up the expensive app database to do more valuable work.

I appreciate you taking the time to read about this, and hope you'll take a look at Wandrer and use it to explore your city. Think about that road by your house that you've never been down in all these years. Go check it out!
