---
layout: post
title:  '"100% routing" is live'
date:   2026-04-02
author: Craig
tags:  updates
cover: "/assets/images/2026-04-02-100-routing/route-header.webp"
---

As much fun as it is to go knock out a bunch of untraveled roads, sometimes you just want to do something without a ton of planning. Wandrer now has "100% routing" tools for you, which will let you easily make a route that covers every road in an area all in one go.

# What is this?

This problem is sometimes called ["Chinese postman"](https://en.wikipedia.org/wiki/Chinese_postman_problem) routing, after the [mathematician](https://en.wikipedia.org/wiki/Meigu_Guan) that first proposed the problem: suppose you're a postal carrier, and you need to travel down every street in an area to deliver mail. What's the most efficient way to do so?

100% routing in Wandrer is implemented in a way that doesn't necessarily produce the optimal/shortest route, but rather that it produces a "plausible" route: something similar to what a human would do. A lot of times this is actaully quite close to optimal, but not striving for optimal means that generating routes for bigger areas becomes more feasible.

In general, 100% routes tend to be around 25-33% bigger than the total distance within the area. This is going to vary depending on the number of dead-end and one-way roads, but is a decent rule: 10 km of road will require 12-13km of travel.

As an aside, the "Chinese postman problem" falls in the realm *graph theory*, a discipline that seems to come up with very practical names for its problems. There's also the ["7 Bridges of Koenigsburg problem"](https://en.wikipedia.org/wiki/Seven_Bridges_of_K%C3%B6nigsberg) (is it possible to cross 7 bridges in the town of Koenigsberg once and only once? No, it's not.), the "New York street sweeper problem" (a Chinese Postman variant where you have a lot of one-way streets and turn restrictions), and the "Windy street sweeper problem" (a Chinese Postman variant where some directions easier to travel than others, because of wind/traffic/elevation/etc.).

100% routing is available only for upgraded Wandrer users, and only on desktop.

To create a route, open the toolbar in the top right of the big map and choose Route Generator:

![](/assets/images/2026-04-02-100-routing/route-generator.webp){:style="width: 50%; display:block; margin-left:auto; margin-right:auto"}

Once there, you can search for a place by name or draw your own shape by clicking the pencil icon:



You can also make a route from a given selected area:

![](/assets/images/2026-04-02-100-routing/make-route.webp){:style="width: 50%; display:block; margin-left:auto; margin-right:auto"}

One thing about drawing the boundary: the **start** and **end** points of a road must be contained within your area to be routable. If either one is outside of your boundary, even by a little bit, it will not be included.

However you get there, you'll then be presented with a window to set some parameters about your route: activity type, start point, end point, and whether to try to avoid already-traveled roads. Avoiding already-traveled roads is a "best-effort" attempt and may still result in covering already-traveled roads.

![](/assets/images/2026-04-02-100-routing/route-window.webp){:style="width: 50%; display:block; margin-left:auto; margin-right:auto"}

Place your markers and click "Create Route":

![](/assets/images/2026-04-02-100-routing/route-with-markers.webp){:style="display:block; margin-left:auto; margin-right:auto"}

Once it's created, you can "play" the sequence of the route (since they can often cross over themselves) and download a text cuesheet (recommended!) as well as GPX file of the route:

![](/assets/images/2026-04-02-100-routing/route-progress.webp){:style="display:block; margin-left:auto; margin-right:auto"}

Enjoy! Definitely check out how the route proceeds before popping it on to your computer and going for it. The algorithms can make mistakes, but oftentimes there is a method to their madness. Following a machine's instructions can feel weird and it might not do things in an order that is intuitive.

And as always, let me know any way that I can improve this for you.
