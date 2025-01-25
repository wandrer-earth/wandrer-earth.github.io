---
layout: post
title:  'Wandrer + RideWithGPS is live!'
date:   2025-01-23
author: Craig
tags:  updates
cover: "/assets/images/2025-01-23-wandrer-ridewithgps/wandrer-ridewithgps.svg"
---

Hey folks! As a follow-up to [this post](https://news.wandrer.earth/2024/12/09/strava-wandrer-changes.html), Wandrer can now be used with RideWithGPS! You can link your RideWithGPS account at your [Wandrer settings page](https://wandrer.earth/settings#linked):

![](/assets/images/2025-01-23-wandrer-ridewithgps/link.png){:style="width: 85%; display:block; margin-left:auto; margin-right:auto"}

The folks at RideWithGPS have been working hard these past few weeks getting some final bits in to place for Wandrer compatibility and I'm pleased to report the current status is: pretty good! Things seem solid on their end, but since this is Wandrer's first external data connection aside from Strava, I'm still working out a few quirks. For what it's worth, there are currently over 200 Wandrers linked to RideWithGPS and I'm fielding a lot fewer bug reports about it these days than I was a few weeks ago. 😬

If you want to give it a shot, RideWithGPS has a helpful data import guide [here](https://ridewithgps.com/journal/7602-migrate-your-ride-data-to-ride-with-gps).

RideWithGPS are also offering a free 30-day premium upgrade for folks that connect their RideWithGPS account on Wandrer, and this will give you access to their activity center tools, allowing for bulk updating of activity types, gear, etc. for if you're doing a large data import.

## Duplicate activity data

Now that Wandrer supports data coming in from multiple sources, there comes the possibility of syncing the same activity from different places. The current plan is that Wandrer will de-duplicate any activities that occur within +/- 1 minute of each other (on the basis that you can only be in one place at a time).

So the next question is: which activity stays and which gets removed? As things are right now, Wandrer will prefer a RideWithGPS version of an activity over any other version, and that's in large part because of RideWithGPS's nice data policies.

If you've paid attention to the difficulty that is updating the map data on Wandrer, one of the things that has come up in the past with Strava is that Wandrer is forbidden from keeping a copy of your raw Strava GPS data. Furthermore, Wandrer also has a data request limit with Strava, dictating how many data requests Wandrer could make at a time. These limitations have complicated and delayed the updating of folks to the latest map data. Neither of those restrictions are in place with RideWithGPS, so map updates should hopefully go faster and smoother for RideWithGPS users in the future.

And, as mentioned in the previous post, accounts linked to RideWithGPS don't have viewing restrictions on your Wandrer map, so other wandrers will be able to check out your progress as before.
