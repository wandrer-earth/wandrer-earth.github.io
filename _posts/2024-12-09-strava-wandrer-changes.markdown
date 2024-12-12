---
layout: post
title:  'Changes to the Wandrer Data Connections'
date:   2024-12-09
author: Pearl
tags: features updates
cover: "/assets/images/2024-12-09-strava-wandrer-changes/transition.webp"
---

Well, it's been a busy month here at Wandrer HQ. In mid-November, [Strava announced a change](https://press.strava.com/articles/updates-to-stravas-api-agreement) to their API terms. In the interest of stronger user privacy, they added a restriction that any third-party apps may only display a user's Strava activity data to that specific user. If you missed it at the time, this announcement caused quite a stir on Wandrer forums (Reddit [1](https://www.reddit.com/r/wandrer/comments/1guaoo1/new_strava_connected_apps_policy/) [2](https://www.reddit.com/r/wandrer/comments/1guih12/is_this_the_end_of_wandrer_leaderboards/), [Strava](https://www.strava.com/clubs/528504/posts/33559707)) and social media (a summary is available on [Tech Radar](https://www.techradar.com/health-fitness/strava-could-soon-stop-working-with-some-of-your-third-party-apps-heres-what-you-need-to-know)). At that time, Strava reached out to Craig to discuss their new policies and what they specifically want us to change.

First, the Strava API team mandated that new users be asked to actively opt in to the public leaderboards. Easy enough.

Second, they let us know that if a user's Wandrer map was generated using Strava data, then the street-level data should not be visible to any other users. Here at Wandrer, we disagree that making your Wandrer map visible to other users violates the new terms. We create a road network using OpenStreetMap data and then match GPS traces obtained from Strava to that network. When you view the Wandrer map, the raw data from Strava is never shown. We offered to make Wandrer maps opt-in by default with periodic check-ins to confirm continued sharing, but the Strava team did not agree to this proposal.

As a result, if your Wandrer map was generated using Strava data, then it will show only achievements and not road-level detail to other users beginning in mid-December.

![](/assets/images/2024-12-09-strava-wandrer-changes/example-big-map.webp){:style="width: 85%; display:block; margin-left:auto; margin-right:auto"}
<figcaption>The less-detailed view when viewing someone else's map going forward
</figcaption>{:style="width: 85%; display:block; margin-left:auto; margin-right:auto"}

Further, we expect this change to affect participation in the leaderboard competitions. We think it's important for an individual's detailed Wandrer map to be visible if they're competing on a leaderboard as a check to discourage cheating. After a few months of transition time, it seems possible that we'll have to make leaderboard competitions only open to those Wandrers whose data comes from sources other than Strava.

Which gets to the next point: yes, sources other than Strava! Because we've heard from so many of you who love viewing and sharing your Wandrer map, we're adding new ways to import activity data into Wandrer. You will soon be able to link your [RideWithGPS](https://ridewithgps.com/) and [Garmin](https://connect.garmin.com/) accounts to Wandrer. If you choose to connect these accounts, we will generate your Wandrer map using data from these sources and you can freely share your map without violating Strava's terms. We plan to add more API connections in the future, so be in touch if you have any particular requests.

What does this mean in summary?
1. Wandrer maps will share achievement-level data only starting mid-December, 2024.
2. Leaderboard visibility is now opt-in by default for new Wandrers.
3. Leaderboard competitions will likely change in the next few months to be available only to Wandrers with a non-Strava account linked. Please let us know your feedback on if this seems like an important move.
4. It will soon be possible to link your RideWithGPS and Garmin accounts to Wandrer.
5. If competing in the leaderboards or sharing your detailed Wandrer map are not important to you, then you don't need to do anything.

Finally, we appreciate your support! We received so many kind messages when it became apparent that we'd need to make changes to comply with Strava's new terms and they really boost morale. Our goal is to make this transition as seamless as possible as we comply with Strava's terms and add new features to make Wandrer better.
