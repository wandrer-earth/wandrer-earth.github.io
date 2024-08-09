---
layout: post
title:  "Summer in the city"
date:   2024-07-23
author: Craig
tags: updates
cover: "/assets/images/2024-07-23-summer/hotdog.jpg"
---

Hi folks! Been a while since we caught up, so I wanted to let yall know what's been going on in Wandrerworld:

### All of Singapore

In case you missed it, we had our first country completion on Wandrer! You can read all about it [here](https://news.wandrer.earth/2024/05/24/completing-an-entire-country.html).

### New big map in place

![](/assets/images/2024-07-23-summer/my_places.png){:style="width: 100%; display:block; margin-left:auto; margin-right:auto"}

You've probably already seen this, but just to make it official: the [big map](https://wandrer.earth/dashboard/my_places) page has been updated. It's got some new features (focus on an area, zoom to an area), and improved features too (viewing your progress during a given time period should be much faster, can toggle paved + unpaved roads), and hopefully easier navigation in general. Let me know your thoughts!

### Wandrer routing tools

I've had some good progress in the past few months with Wandrer routing tools. Two things you might want to see:

#### Routes covering every road an area

![](/assets/images/2024-07-23-summer/area.png){:style="width: 100%; display:block; margin-left:auto; margin-right:auto"}

Routes of this style are sometimes called ["Chinese Postman"](https://en.wikipedia.org/wiki/Chinese_postman_problem) style routes after a Chinese mathematician that first posed the problem: what's the optimal route for a mail carrier to travel in order to deliver mail to every postbox? Or, in graph terms: what's the optimal route to visit every edge in a graph at least once?

This has been in beta on Wandrer for a while now, honestly it might just stay there unless tons of folks come out to ask for it. Feedback on it so far has been kind of lukewarm maybe? Not everything can be a winner I guess.

#### Routes optimizing new roads from point to point

Still in progress, so I'm just gonna leave this here for now:

![](/assets/images/2024-07-23-summer/point-to-point.png){:style="width: 100%; display:block; margin-left:auto; margin-right:auto"}

### Wandrer Garmin developments

![](/assets/images/2024-07-23-summer/garmin.jpg){:style="width: 100%; display:block; margin-left:auto; margin-right:auto"}

I've got good progress on a Wandrer app for Garmin devices in the near future. This would mean that you no longer have to download Garmin maps to your computer and load them on to your device. I've got something functional here, but Garmins have just enough constraints on their power/storage/battery/network that I'm not sure if it will work for everything.

It's kind of fun writing software for Garmin devices though because it's a real change from the rest of Wandrer, where if something complex or time-consuming needs to happen, I can mostly spin up a bunch of other servers and have as many resources as I need.

Garmins, on the other hand, are like "You want memory? I'll give you 128KB. Final offer. Internet? Best I can do is a Bluetooth connection to your phone. Hope it's got service." and you have to be a bit more creative in how you solve things.

### Progress in simplifying parallel roads

![](/assets/images/2024-07-23-summer/taipei.png){:style="width: 100%; display:block; margin-left:auto; margin-right:auto"}

One of the annoying things about Wandrer (for you and for me) are areas with lots of parallel paths: a divided highway with cycle paths on either side of it, for instance, would be 4 separate paths on Wandrer, each covering basically the same area.

This is tricky to address because, as humans, we can just look at the map and see what's going on. But from a software point of view, it's hard to formalize "These are parallel. Those aren't." since there are lots of edge cases: a path that starts out next to a road but then drifts off in to the woods, or it starts out next to the road but then the road turns and the path continues straight and crosses the road, etc. So it's been hard for me to figure out a good approach.

But there's some low-hanging fruit we can start with, and I'm going to start rolling out some deduplication features in the next map update. The first one will be pretty simple: two sections of road within X meters of each other, each with the same name, each one-way in opposite directions, and each having no side connections. There's obviously a lot of conditions there, but it's a start, and things hopefully can be relaxed / broadened from there.

An example of what I'm talking about:
![](/assets/images/2024-07-23-summer/dedup.png){:style="width: 100%; display:block; margin-left:auto; margin-right:auto"}
<figcaption>Before/after
</figcaption>{:style="width: 85%; display:block; margin-left:auto; margin-right:auto"}

Now, traveling either direction of the road should earn you credit for the central respresentative section.

Still lots of things to figure out here, but it's progress and will hopefully make Wandrer more fun as you spend less time being frustrated and trying to get that last little bit.

### New map data as of July 2, 2024

If you're upgraded, you should have new map data available for you. Request the update on your [settings page](https://wandrer.earth/settings). This should also fix a few issues that were present in the previous (May 3rd) map data, specifically that a bunch of sidewalks were erroneously included.

### National forests

![](/assets/images/2024-07-23-summer/forest-service.svg){:style="max-height: 300px; display:block; margin-left:auto; margin-right:auto"}

It's taking a while for this to get in place with the map update also happening, but I'm adding all of the US National Forests to Wandrer. Some of these places are quite small (Tuskegee National Forest: 70 miles / 112 km) to really big (Humboldt-Toiyabe National Forest: 10152 mi / 16334 km). Let me know if there are any other areas you'd like to see added.


### We're going on an adventure!

![](/assets/images/2024-07-23-summer/gonefishin.jpg){:style="display:block; margin-left:auto; margin-right:auto"}

Back when Pearl was pregnant, we were looking for bike tours in Europe and a Wandrer user suggested the [Neckar River bike path](https://www.adfc-radtourismus.de/neckartal-radweg/). It's a really lovely river path and we rode it from the start at Mannheim down to Stuttgart, which is not all that far, but hey, give us a break we only had 3 days and Pearl was 6 months pregnant.

Now that she's not pregnant, we are returning to Stuttgart and trying to bike to Spain. Our baby is now 2 years old, and weighs an extra 15 lbs / 7 kg more than she did during our [last tour](https://news.wandrer.earth/2023/03/29/bike-touring-baby.html) so I'm expecting that this will take us most of the month of August.

Because we'll be on the road, August will be "summer hours" for Wandrer and things are going to be a little slower-paced. I'll definitely be working and answering emails, but also spending more time towing a baby up a mountain, working on my pronounciation of ü and ö, and figuring out where we're going to sleep that night.

Our tentative route is here:

<iframe src="https://ridewithgps.com/embeds?type=route&id=47780440&metricUnits=true&sampleGraph=true" style="width: 1px; min-width: 100%; height: 700px; border: none;" scrolling="no"></iframe>

Please get in touch if you live nearby and would like to meet up! Our pace is likely going to be pretty slow, but it'd be great to meet other Wandrers I'll have extra Wandrer patches+stickers on hand. Or if you know of nice places to stay, quiet roads, excellent bakeries on our way, or if you've actually seen the Joe Pesci + Danny Glover "Gone Fishin'" movie -- 4% on Rotten Tomatoes!

*UPDATE*: Since I originally started this blog post a few weeks ago, we've started our tour and have made it to Zurich! It's also been a bit rough start: on our first day, my computer broke, a friend had their phone stolen and recovered, my wife a slow speed crash in front of an oncoming car, and we thought our baby broke her leg and had to travel to several German hospitals late at night. But now we're doing pretty good!

### Elsewhere

Fun article about [what is captured when you draw a map](https://escapethealgorithm.substack.com/p/should-this-be-a-map-or-500-maps).
