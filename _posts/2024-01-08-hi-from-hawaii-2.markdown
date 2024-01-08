---
layout: post
title:  "Wandrer December 2023 update: Hi from Hawaii 2"
date:   2024-01-08
author: Craig
tags: updates
cover: "/assets/images/2024-01-08-hi-from-hawaii-2/hawaii-2-50.png"
---

Hello from the Wandrer Worldwide Headquarters, currently located in beautiful [Hawaii 2](https://www.openstreetmap.org/way/150538916) in Waldo County, Maine, USA. Never heard of Hawaii 2? Well, it's kind of exclusive. We don't like people finding out about it really. Maybe think of it as an exciting sequel to normal boring Hawaii?

We drove past the island of Hawaii 2 this summer on the way to [Liberty Graphics](https://lgtees.com/) and, as someone who looks at maps all day, I filed it away in my list of interesting places in the world, and referencing it somehow in this blog post seemed like fun.

![](/assets/images/2024-01-08-hi-from-hawaii-2/liberty.jpg){:style="width: 85%; display:block; margin-left:auto; margin-right:auto"}
<figcaption>Liberty Graphics, with a message we can all support
</figcaption>{:style="width: 85%; display:block; margin-left:auto; margin-right:auto"}

But apparently the story is [even weirder](https://en.wikipedia.org/wiki/Hawaii_2) than I thought, as the island was actually purchased in 2014 as part of a joke (?) fundraiser by the company behind the game Cards Against Humanity. They offered claims to an individual one-square-foot parcel on the island as a donation prize and this got them in all sorts of trouble with code violations around commercial use of the island. The town of Liberty (population 934, 2022 revenue of [$3.5M](https://libertymaine.us/wp-content/uploads/2023/03/2022-Annual-Report.pdf)), threatened Cards Against Humanity with fines of $625M per day until those violations were fixed.

So maybe Hawaii 2 is actually pretty exclusive? Liberty, Maine certainly puts a high price tag on people being there.

Anyway, some Wandrer updates:

### Wandrer extension + RideWithGPS
The [RideWithGPS](https://ridewithgps.com) folks have been busy at work updating their mapping infrastructure, and this is likely completely unnoticeable to you, but a lot has been going on behind the scenes over there. It was hard to modify the Wandrer browser extension ([Chrome](https://chrome.google.com/webstore/detail/wandrer-map-overlay/nmcamjnbjejckmdbobepfjdehbfillan) | [Firefox](https://addons.mozilla.org/en-US/firefox/addon/wandrer-map-overlay/)) to keep up for a while. The extension was broken for a lot of November, but it's back to functional now.

And if you've had performance issues with RWGPS and the Wandrer extension in the past, give it another shot: big parts of it were simplified and it hopefully should run much smoother for you (at least on the non-Google layers).

### Map data update
There's new map data available, featuring OpenStreetMap data as of November 3, 2023. It's currently available for upgraded users only. If you haven't switched over already, you can do so at your [settings page](https://wandrer.earth/settings#preferences) in the "Your Map" section. Most of the initial backlog is cleared out, so it shouldn't take more than a day or two to get you switched over.

This map update is an entirely new planet rather than piecemeal updates of requested areas, and was much easier for me. I'd like to keep doing things this way going forward. It lets me get new data out to folks faster and honestly frees up a ton of my mental space to work on other aspects of Wandrer. It does have the side effect of meaning that we Wandrer users will no longer all be using the exact same map data, but given the volume of changes in OpenStreetMap and the limited access I have to Strava data (can't store raw GPS data, can only make X data requests per day), it seems like trying to migrate everyone to new data all together is just no longer feasible.

The different map datasets issue also brings up an interesting OpenStreetMap trend: where is OpenStreetMap changing the most?

In this most recent update, the entire planet gained **4.23M** new km / **2.62M** new miles of bikeable/walkable roads and paths. Of those 4.23 million new km, 540,540 were in India, 470,579 were in China, 472,973 were in East Africa, 227,758 were in West Africa, 196,945 were in Russia, and 190,530 were in Brazil. That's accounts for half of the new distance right there, and it's great to see "undermapped" places getting more OSM coverage.

### Items for the next map update

I'm planning to do another map update sometime in January, and there are a few tweaks planned for this next one. None of this is set in stone, but your thoughts are welcome.

* Start removing ways tagged `access=delivery`
* Start including ways tagged `access=permit`. Like many OpenStreetMap things, usage of this tag is not 100% identical everywhere, but according to the [wiki](https://wiki.openstreetmap.org/wiki/Tag:access%3Dpermit), "this tag should be used in cases where a permit is required, but is routinely granted to everyone requesting it." That feels like a manageable situation.
* Start removing ways tagged `bicycle=yes` and `footway=sidewalk` in the US. There are a few cities in the United States that allow bicycles to ride on the sidewalk (in addition to the road) and some of these sidewalks are tagged `bicycle=yes`, which is redundant.
* Addition of `service=alley` in Germany. This one definitely needs some further examination!

### Big map redesign
![](/assets/images/2024-01-08-hi-from-hawaii-2/my_places.png){:style="width: 85%; display:block; margin-left:auto; margin-right:auto"}
One of the things I've been chipping away at is getting Wandrer's big map redesigned. The current big map is...fine. It's functional, and people seem to put up with its quirks, but it could be a lot better:
* The mobile experience is not great
* Viewing your achievement progress is awkward
* Navigating to specific places is difficult
* Changing activity types requires a page reload
* No legend
* There are two different maps on the site: your big map, and your "dashboard" for a given area, and they each have different info
* It's busy: there's a lot on the screen already and not much room for new Wandrer features

So I'm working on fixing that. It's very much a work in progress, but I welcome feedback on its current direction. You can see it for yourself [here](https://wandrer.earth/dashboard/my_places).

There are two things that I know are missing: the mini-leaderboard for achievement areas, and the ability to view your map progress over a certain time window. These are coming.

I've also received a fair amount of feedback from beta testers already, so here are a few things that I'm planning on addressing:
* Unpaved traveled roads aren't styled properly
* Move map controls back to the left side on mobile?
* Make viewing your achievement stats take up less of the screen on mobile
* Turning off untraveled roads should turn off all untraveled road variants
* Activity type selection might make more sense in the layers/legend area

### Karoo compass updates
If you're a user of the Karoo app, you may have occasionally noticed that the map orientation in the Wandrer app differs substantially from that in the Karoo app itself. This is a small thing, but it can be quite disorienting. I believe the issue is fixed, and a [new version](https://wandrer.earth/karoo) of the Wandrer Karoo app (1.6) is now available.

### End-of-year summaries are coming!
Maybe this is weird, but I like waiting until the year is actually over before getting folks their yearly update. So the summaries are in progress and you'll get a notification on your dashboard when they're ready.

### Friends and Accomplishments
* Luke Tuttle published a [nice article](https://www.ultrarunningdestinations.com/home/using-wandrerearth-to-motivate-your-discovery-of-new-trails-not-just-log-miles) about Wandrer recently.

* Matt completed [99% of Baltimore!](https://www.strava.com/clubs/528504/posts/27145837)

* Megan completed [99% of San Mateo County!](https://www.strava.com/clubs/528504/posts/27217779) -- this one started during the pandemic!

Happy wandrering!

Craig
