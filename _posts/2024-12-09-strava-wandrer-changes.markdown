---
layout: post
title:  'Changes to the Wandrer Data Connections'
date:   2024-12-09
author: Pearl
tags: features updates
cover: "/assets/images/2024-12-09-strava-wandrer-changes/example-big-map.jpg"
---

Well, it's been a busy month here at Wandrer HQ. In mid-November, [Strava announced a change](https://press.strava.com/articles/updates-to-stravas-api-agreement) to their API terms. In the interest of stronger user privacy, they added a restriction that any third-party apps may only display a user's Strava activity data to that specific user. If you missed it at the time, this announcement caused quite a stir on Wandrer forums (Reddit [1](https://www.reddit.com/r/wandrer/comments/1guaoo1/new_strava_connected_apps_policy/) [2](https://www.reddit.com/r/wandrer/comments/1guih12/is_this_the_end_of_wandrer_leaderboards/), [Strava](https://www.strava.com/clubs/528504/posts/33559707)) and social media (a summary is available on [Tech Radar](https://www.techradar.com/health-fitness/strava-could-soon-stop-working-with-some-of-your-third-party-apps-heres-what-you-need-to-know)). At that time, Strava reached out to Craig to discuss their new policies and what they specifically want us to change.

First, the Strava API team mandated that new users be asked to actively opt in to the public leaderboards. Easy enough.

Second, they let us know that if a user's Wandrer map was generated using Strava data, then the street-level data should not be visible to any other users. Here at Wandrer, we disagree that making your Wandrer map visible to other users violates the new terms. We create a road network using OpenStreetMap data and then match GPS traces obtained from Strava to that network. When you view the Wandrer map, the raw data from Strava is never shown. We offered to make Wandrer maps opt-in by default with periodic check-ins to confirm continued sharing, but the Strava team did not agree to this proposal.

As a result, if your Wandrer map was generated using Strava data, then it show only achievements and not individual roads to other users beginning in mid-December.

![](/assets/images/2024-12-09-strava-wandrer-changes/example-big-map.jpg){:style="width: 85%; display:block; margin-left:auto; margin-right:auto"}
<figcaption>The new default shared Wandrer map for Strava users
</figcaption>{:style="width: 85%; display:block; margin-left:auto; margin-right:auto"}

Further, we expect this change to affect participation in the public leaderboards. We think it's important for an individual's detailed Wandrer map to be visible if they're competing on a leaderboard as a check to discourage cheating. After a few months of transition time (which will allow us to support more alternate services and give you time to link your accounts), we will likely make public leaderboards only open to those Wandrers whose data comes from sources other than Strava. We'll be sure to give a heads up before this change happens so that everyone who wants to has a chance to make the switch.

Yes, sources other than Strava! Because we've heard from so many of you who love sharing your detailed maps, we're adding new ways to import GPS activity data into Wandrer. You can now connect your [Ride with GPS](https://ridewithgps.com/) account on your Wandrer [Settings page](https://wandrer.earth/settings). If you add a Ride with GPS account and unlink your Strava account, then your detailed Big Map with street level data will be visible to other users after a few days of data transition time.

A few important notes specific to Ride with GPS: at the moment, any activities imported to Ride with GPS will be processed as "bike" activities -- even if they're labeled as a "run" in Ride with GPS. This relates to how the data is transferred from Ride with GPS and should be fixed in the near future. Second, you can bulk import historical data into Ride with GPS. Instructions are available on [Ride with GPS Journal](https://ridewithgps.com/journal/7602-migrate-your-ride-data-to-ride-with-gps).

In addition to Ride with GPS, we are actively working on adding more API connections, such as Garmin, Wahoo, Polar, Coros, etc. We prioritize APIs based on your input, so please do [email Craig](mailto: craig@wandrer.earth) if there's a service you'd like to connect.

What does this mean in summary?
1. Wandrer maps will share achievement level data only starting mid December 2024.
2. Public leaderboards are now opt-in by default for new Wandrers.
3. Public leaderboards will likely be only available to Wandrers with another account linked in the next 3-6 months.
4. If you'd like to share your detailed Wandrer map, you must connect another account to Wandrer and unlink your Strava account on your [Wandrer Settings page](https://wandrer.earth/settings).
5. If competing in public leaderboards or sharing your detailed Wandrer map are not important to you, then you don't need to do anything.

Finally, we appreciate your support! We received so many kind messages when it became apparent that we'd need to make changes to comply with Strava's new terms and they really boost morale. Our goal is to make this transition as seamless as possible as we comply with Strava's terms and add new features to make Wandrer better.
