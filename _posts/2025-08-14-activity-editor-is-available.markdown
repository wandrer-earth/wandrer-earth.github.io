---
layout: post
title:  'Activity editor is available'
date:   2025-08-14
author: Craig
tags:  updates
cover: "/assets/images/2025-08-14-activity-editor/straighten-1.webp"
---

One of the more annoying aspects of Wandrer (for you and for me) is when your activities don't match correctly: you traveled on a road or path but didn't get credit for it.

Sometimes this is just because the road/path wasn't included in Wandrer's dataset, which can happen for a variety of reasons. But often it's because of a GPS error or algorithm error: you were in the right area, but your GPS didn't record it properly, and/or Wandrer put you on a different road than you expected.

Rather than spend a lot of time perfecting Wandrer's matching algorithm (which, to be clear, I have also tried, but is difficult for a variety of reasons), here's a simple solution: let you edit the activity trace so that it falls in the correct place. It'd be great if the algorithm were able to get this right the first time around, but as a fallback, tweaking the activity seems a lot easier than having to go back out to the area in question and travel it again.

And there are some situations where you don't necessarily want the matching algorithm to be right. Is there a busy road with a bike lane next to it, and both are included on Wandrer? Travel the bike lane twice and move one of the lines over to the busy road and get credit for that as well. Wandrer should be fun, not frustrating.

To start editing, visit the page of any activity:

![](/assets/images/2025-08-14-activity-editor/open-activity.webp){:style="width: 100%; display:block; margin-left:auto; margin-right:auto"}

And click the pencil icon in the bottom left:

![](/assets/images/2025-08-14-activity-editor/pencil.webp){:style="display:block; margin-left:auto; margin-right:auto"}

It will start edit mode and open a small window with information about your edits:

![](/assets/images/2025-08-14-activity-editor/edit.webp){:style="width: 100%; display:block; margin-left:auto; margin-right:auto"}

There's an info window available with the "i" icon, but in short, editing consists of selecting a single point (or multiple points) and dragging it to its new location.

You can select multiple points by holding shift and either clicking and drawing a box around the points in question, or by holding shift and selecting multiple point from your trace:

![](/assets/images/2025-08-14-activity-editor/multiple-points.webp){:style="width: 100%; display:block; margin-left:auto; margin-right:auto"}

There's also a "straighten" tool that will move all selected points on to the line drawn between the first and last point:

![](/assets/images/2025-08-14-activity-editor/straighten-1.webp){:style="width: 100%; display:block; margin-left:auto; margin-right:auto"}

![](/assets/images/2025-08-14-activity-editor/straighten-2.webp){:style="width: 100%; display:block; margin-left:auto; margin-right:auto"}

When you're done editing, click Save, and your changes will be processed. The page needs to be reloaded in order to view the changes.

![](/assets/images/2025-08-14-activity-editor/finished-editing.webp){:style="width: 100%; display:block; margin-left:auto; margin-right:auto"}

This is currently an upgraded-only (and desktop-only) feature. Happy editing!
