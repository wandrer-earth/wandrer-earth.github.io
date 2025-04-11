---
layout: post
title:  "What's the longest street name in the world?"
date:   2025-03-30
author: Craig
tags:  updates
cover: "/assets/images/2025-03-30-longest-street-name/call-me-by-your-name.jpg"
---

Wandrer depends on [OpenStreetMap](https://openstreetmap.org){:target="_blank"} in some very crucial and specific ways. OSM is the source of all of the road geometry data and access rules used in Wandrer, as well as many of the boundaries used in Wandrer achievements. So I spend a lot of time thinking about those particular things.

But OpenStreetMap is such an amazing project and so much bigger than just the portions that Wandrer uses, so I thought it would be fun to look at some other parts of OSM that I might not notice normally. One question I had recently is: **what's the longest street name in the world?**

## Quick OpenStreetMap background

![](/assets/images/2025-03-30-longest-street-name/osm.png){:style="width: 100%; display:block; margin-left:auto; margin-right:auto"}
<figcaption>A lit residential road (Rue 5.16) in Burkina Faso with speed limit of 50 kph.
</figcaption>

OpenStreetMap is a free map of the world that anyone can edit. It's kind of like Wikipedia in that it's 1) maintained by volunteers and 2) surprisingly high-quality.

There are 3 main objects in OpenStreetMap:
1. **nodes**: used for point features, like "there's a water fountain here", or "there's a gate here".
2. **ways**: for line features, such as roads, train tracks, power lines, etc.
3. **relations**: for area features like boundaries, lakes, buildings etc.

Since we're looking at streets and their names, we'll be dealing with ways.

Every node/way/relation can have data associated with it: this way is a road and it's a motorway and it has 6 lanes and it's name is Route 220. Or this way is forest road and it's 2 meters wide and it's unpaved and it's only open between May and September. Data about each way in OSM  is stored as "tags". So you might have a `surface` tag that says `asphalt`, or a `name` tag that says `Main Street`, or a `lanes` tag that says `4`.

## Caveats

To be clear, when talking about "street name" here, I am including basically any named, travelable path in the "street" category, even if they might not normally be considered streets. This would be things like bike paths, pedestrian paths, farm roads, walkways, and hiking trails.

There is also some filtering that Wandrer does to remove ways that aren't bikeable/walkable. This means that a lot of `highway=service/footway/motorway/...` ways, and private (`access=private/no/customers/military/...`) ways aren't being looked at here.

Determining "longest street name" is also probably not fair to languages like Chinese, where something like "大學" is composed of 2 characters, but other languages would express this as "college" or "university", getting 7 or 10 characters.

## What's in a `name` (tag)?

The real question we want to answer first here is: what counts as a street name?

One way of thinking about this is that a street's name is anything found in the `name` tag on OpenStreetMap. This is probably the most literal defintion of "street name", but there are a lot of places in the world where what's in the `name` tag doesn't really line up with what we would think of as a "street name". A few examples:

* [Way 361548340](https://www.openstreetmap.org/way/361548340){:target="_blank"}: translated as "Trenches and machine gun nests from the Spanish Civil War (Rebel faction)" (73 characters)
* [Way 1145040903](https://www.openstreetmap.org/way/1145040903){:target="_blank"}: which Google translates to "motorway (access roads to sites H23, H24, H25, H26, P13, PH2, 3, VZU of the industrial turkey farming complex in the village of Ust-Karemsha, Nizhnelomovsky District, Penza Region" (179 characters)
* [Way 621398853](https://www.openstreetmap.org/way/621398853){:target="_blank"}: translated to "Brick paving unpaved road from Sheikh Par Bridge to Bahr Bonia 4km" (66 characters)

And so forth. A lot of these are very utilitarian "names" that are probably better placed in the OpenStreetMap `description` tag. But for the sake of throughness, let's crown some winners here:

![](/assets/images/2025-03-30-longest-street-name/first-name.png){:style="width: 100%; display:block; margin-left:auto; margin-right:auto"}
<figcaption>Way 244285273
</figcaption>
1. 👑 In first place, at 255 characters, we have [way 244285273](https://www.openstreetmap.org/way/244285273){:target="_blank"}: "lundi 10/02/2025 de 10h00 à 11h00 (heure française) mardi 11/02/2025 de 11h00 à 12h00 (heure française) mercredi 12/02/2025 de 11h00 à 12h00 (heure française)  lundi 17/02/2025 de 10h00 à 11h00 (heure française) mardi 18/02/2025 de 11h00 à 12h00 (heure fr".

    I gotta say, I find this pretty dissatisfying. It's just a bunch of out-of-date park hours. And they're in French, even though this little road is in Wisconsin. Boo.

![](/assets/images/2025-03-30-longest-street-name/second-name.png){:style="width: 100%; display:block; margin-left:auto; margin-right:auto"}
<figcaption>Way 402233662
</figcaption>

2. 🏆 Second place, at 238 characters is [way 402233662](https://www.openstreetmap.org/way/402233662){:target="_blank"}: translated as "Educational trail, Balatonfelvidéki ÍNational Park: a dirt road connecting the section along the embankment with the final stop, the gravel reef, Élet-sziget, crossing the floodplain. Accessible by off-road vehicle (although it is difficult to get there on the road under the ruined embankment.)".

    Now this I can get in to. You get an entire narrative journey! I can practically visualize the scene in my head. None of this at all is a real street name of course, but it's way better than boring park hours.

![](/assets/images/2025-03-30-longest-street-name/third-name.png){:style="width: 100%; display:block; margin-left:auto; margin-right:auto"}
<figcaption>Way 549249106
</figcaption>

3. 🏅 3rd place, at 230 characters is [way 549249106](https://www.openstreetmap.org/way/549249106){:target="_blank"}: "SECRETS OF SPANISH FLORIDA - A SECRETS OF THE DEAD SPECIAL Archaeologists, scientists and historians reveal the little-known history of America's Spanish colonists who settled in Florida in 1565, long before Jamestown or Plymouth".

    There's something very charming here: the all-caps, the _pulling-back-the-curtain_ of it. Is it a sandy track in the swamp or a podcast? It's great either way. (Turns out it's actaully a [PBS episode](https://www.pbs.org/wnet/secrets/secrets-spanish-florida-synopsis/3626/), and this way is in Alaska!)

So although there's a bunch of weird and wrong stuff here, I think probably most names are correct in OSM, and I've started tracking them for fun on Wandrer. You can see your longest completed street in the points breakdown in your stats at [https://wandrer.earth/dashboard/stats](https://wandrer.earth/dashboard/stats) -- you'll earn 1 point per character! Our current leader is [way 550626032](https://www.openstreetmap.org/way/550626032), with 224 points.

## But what about the longest _real_ name?

Surfacing a bunch of mistakes and copy/paste errors is not the most exciting use of OpenStreetMap, so let's tighten up our criteria a bit. What we really want are those streets that are **deliberately named** for something other than their purpose. I recognize there's some subjectivity here. Some roads are just called "Strada Provinciale": it's just a provincial road.

But then there's Willow Lanes and Roberts Avenues and Bahnhofstraßen and Calles Emiliano Zapata, etc. These are what I want.

I haven't found a great way to automate this, so I ended up just looking through lots of records ordered by length. And there's some weirdness here: 1st, 2nd, and 3rd place are all in Oklahoma, USA, and it's not entirely clear which one is the winner. Our candidates:

![](/assets/images/2025-03-30-longest-street-name/woodrow-highway.png){:style="width: 100%; display:block; margin-left:auto; margin-right:auto"}
<figcaption>Retired Army Master Sargeant Woodrow T. Cox – World War II Prisoner of War – Memorial Highway (Google Earth)
</figcaption>

1. 🤷‍♀️ 1st/2nd place, at 93<sup>*</sup> characters long, the [Retired Army Master Sargeant Woodrow T. Cox – World War II Prisoner of War – Memorial Highway](https://www.openstreetmap.org/way/1272380355){:target="_blank"}. Named by act [69 OK Stat § 1698.226](https://law.justia.com/codes/oklahoma/title-69/section-69-1698-226/) of Oklahoma legislature, so very much deliberately named.

![](/assets/images/2025-03-30-longest-street-name/cody-highway.png){:style="width: 100%; display:block; margin-left:auto; margin-right:auto"}
<figcaption>Private First Class Cody Montana Carver, U.S. Army 3rd Infantry Division Memorial Bridge (Google Earth)
</figcaption>

2. 🤔 1st/2nd place, at 88 characters long, the [Private First Class Cody Montana Carver, U.S. Army 3rd Infantry Division Memorial Bridge](https://www.openstreetmap.org/way/165226334){:target="_blank"}. Named by act [69 OK Stat § 1698.34](https://law.justia.com/codes/oklahoma/title-69/section-69-1698-34/) of the Oklahoma legislature.

![](/assets/images/2025-03-30-longest-street-name/hatak-highway.png){:style="width: 100%; display:block; margin-left:auto; margin-right:auto"}
<figcaption>Lance Corporal Hatak-Yuka-Keyu Martin Yearby United States Marine Corps Memorial Bridge (Google Earth)
</figcaption>

3. 🏅 3rd place, at **87** characters long, the [Lance Corporal Hatak-Yuka-Keyu Martin Yearby United States Marine Corps Memorial Bridge](https://www.openstreetmap.org/way/850519220){:target="_blank"}. Named by act [69 OK Stat § 1698.161](https://law.justia.com/codes/oklahoma/title-69/section-69-1698-161/) of the Oklahoma legislature.

Why is it unclear which road is 1st place and which one is 2nd?

The issue is that [way 1272380355](https://www.openstreetmap.org/way/1272380355){:target="_blank"} is named in OpenStreetMap as "Retired Army Master Sargeant Woodrow T. Cox – World War II Prisoner of War – Memorial Highway", 93 characters long.

The official [act of the Oklahoma legislature](https://law.justia.com/codes/oklahoma/title-69/section-69-1698-226/){:target="_blank"}, however, says that the road bridge shall be named "Ret. Army MSGT Woodrow T. Cox – WWII POW – Memorial Highway", which is only 59 characters long! So it's really a matter of how many abbreviations you want to expand.

Rather than dwell on which name is longest and the inevitible split into Team Woodrow versus Team Cody, I thought it would be interesting to folks behind these places.

### Woodrow T. Cox
![](/assets/images/2025-03-30-longest-street-name/woodrow_cox.webp){:style="display:block; margin-left:auto; margin-right:auto"}
<figcaption>Woodrow T. Cox (from the Bataan Project)
</figcaption>
The [Bataan Project](https://bataanproject.com/bataan-project-story/){:target="_blank"} is a fascinating, "old internet" website that documents the history of 192nd and 194th Tank Batallions and how many of the members of these batallions ended up in the [Bataan Death March](https://en.wikipedia.org/wiki/Bataan_Death_March){:target="_blank"} in World War II.

They have a (24,000 word!) [article](https://bataanproject.com/cox-pvt-woodrow-t/){:target="_blank"} about Woodrow T. Cox, with much of it detailing his batallion's voyage to the Philippines, capture by the Japanese, and the conditions at their prison camp. Woodrow doesn't appear a whole lot but it's still an interesting document about an event I had never heard of.

### Cody Montana Carver
![](/assets/images/2025-03-30-longest-street-name/cody_carver.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<figcaption>Cody Montana Carver (from findagrave.com)
</figcaption>
Cody Montana Carver was a 19-year old from the US who liked skateboarding and hanging out with his friends. He was killed in the US invasion of Iraq in 2007, [under a month after he was deployed](https://www.findagrave.com/memorial/22630608/cody_montana-carver).

### Hatak-Yuka-Keyu Martin Yearby
![](/assets/images/2025-03-30-longest-street-name/hatak_yuka_keyu_martin_yearby.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<figcaption>Hatak-Yuka-Keyu Martin Yearby (from findagrave.com)
</figcaption>
[Hatak-Yuka-Keyu Martin Yearby](https://www.findagrave.com/memorial/14296146/hatak_yuka_keyu_martin-yearby) was a 21-year old from the US who grew up attending powwows, where he performed and competed as a traditional Choctaw dancer. He is remembered as a quiet, well-mannered young man who was a good student and person.

So two of the longest named streets on the planet are in Oklahoma, and are both named after kids that were killed in the US invasion of Iraq. What a weird world we live in.

## Rules and regulations

There's another way of calculating a "longest street name" that goes back to Wandrer's preoccupation with the nature of "What is a street?"

Personally speaking, there's some suspension of disbelief required when I'm traveling on a road and that road changes names. There's a part of me that feels like a road should maintain a single name for its entire length.

Here in Atlanta there's a road called Clairmont Road, and when Clairmont Road crosses a particular intersection it becomes "Clair**e**mont Avenue". So just over there it was Clairmont Road and now the exact same road is Clairemont Avenue? And "Clairmont" is spelled differently? Come on.

But we live in a society, and I accept that there are some small injustices that I have to tolerate, even if, especially here in Atlanta, a lot of these street name changes are rooted in [racism](https://www.atlantamagazine.com/list/you-asked-we-answered-34-things-you-probably-dont-know-about-atlanta/why-do-street-names-change-at-ponce/){:target="_blank"}.

What I don't have to tolerate, however, is roads that change names just anywhere they want. I think it's a fair ground rule that if a road is going to change names, it needs to happen at an intersection with another road. You can't just change names at a bridge or a house.

But OpenStreetMap doesn't have any restriction like this. You can just draw things however you like and then name them whatever you want.

So let's modify our search criteria. Previously we were looking at individual OSM ways and finding which had the longest `name` tag. Now let's say a road must keep a stable name between any intersections it has with other roads. If we find multiple names (because we might be spanning multiple OSM ways), we'll join all the names together with a "/" and find the longest one.

So if we had "Way 1" that connected to "Way 2" not at an intersection, their combined name would be "Way 1 / Way 2". With this search, we get some new candidates:

![](/assets/images/2025-03-30-longest-street-name/cayo-santa-maria.png){:style="width: 100%; display:block; margin-left:auto; margin-right:auto"}
<figcaption>Road to Cayo Santa Maria (Google Earth)
</figcaption>

1. 👑 First place, at 457 characters, is this [collection of 71 ways in Cuba](https://overpass-turbo.eu/s/21lw){:target="_blank"}: "Carretera a Cayo Santa María / Pedraplén Cayo Santa María / Puente 10 / Puente 11 / Puente 12 / Puente 13 / Puente 14 / Puente 15 / Puente 16 / Puente 17 / Puente 18 / Puente 19 / Puente 2 / Puente 20 / Puente 21 / Puente 22 / Puente 23 / Puente 24 / Puente 25 / Puente 26 / Puente 27 / Puente 28 / Puente 29 / Puente 3 / Puente 30 / Puente 31 / Puente 32 / Puente 33 / Puente 34 / Puente 35 / Puente 4 / Puente 5 / Puente 6 / Puente 7 / Puente 8 / Puente 9".

    This name is uninspiring on the level of the park hours listing, but look at this road. It just goes out in to the ocean! It looks incredible. I didn't know anything about this road before writing this blog post and now I *really* want to see this place. It's not the most informative, but "dangerousroads.org" has a [short article](https://www.dangerousroads.org/central-america/cuba/5981-el-pedrapl%C3%A9n.html){:target="_blank"} about this road that I had to link to solely because it's from "dangerousroads.org".

![](/assets/images/2025-03-30-longest-street-name/bangladesh.png){:style="width: 100%; display:block; margin-left:auto; margin-right:auto"}
<figcaption>Google Earth
</figcaption>

2. 🏆 Second place, at 376 characters, is this isolated [collection of 12 ways in Bangladesh](https://overpass-turbo.eu/s/21lx){:target="_blank"}: "Chawkidar Bari Theke Idris Khar Bari Porjanta Katcha Rasta / Hawladar Er Barir Uttar Pasher Khaler Sako / Ismail Hawladarer Bari Ebong Hakim Pedar Barir Songjog Setu / Mantur Bari Theke Dakkhin Char-Shahajalal Kheyaghat Porjanta Katcha Rasta / Sattar Hawladar Er Barir Samner Sako / Uttar Charborhan Bazar Er Pul / Volar Border Hote Moti Khan Bari Porjanta 500 km Katcha Rasta"

    I don't even know what to say about this one. That's a lot of names for something that's like 5 km in length. Google translates "Mantur Bari Theke Dakkhin Char-Shahajalal Kheyaghat Porjanta Katcha Rasta" as "Dirt road from Montu's house to South Char-Shahjalal Kheaghat"

![](/assets/images/2025-03-30-longest-street-name/via-ferrata.png){:style="width: 100%; display:block; margin-left:auto; margin-right:auto"}
<figcaption>Google Earth
</figcaption>

3. 🏅 Third place, at 323 characters is this section of [7 via ferrata ways in southeastern France](https://overpass-turbo.eu/s/21lA){:target="_blank"}: "Via Ferrata La Roche à l'Agathe: La Rampe R'Tournes'y Pas / Via Ferrata La Roche à l'Agathe: La Rampe aux Chamoix / Via Ferrata La Roche à l'Agathe: Le Mur / Via Ferrata La Roche à l'Agathe: Le Pont du Calvaire / Via Ferrata La Roche à l'Agathe: Le Rocher du Grand Rappel / Via Ferrata La Roche à l'Agathe: Les Coups de Cul"

    This one feels a little unfair because it has "Via Ferrata La Roche à l'Agathe" (31 characters) in the name of each way. But that's the nature of competition like this. You gotta use any strategy you can to win...3rd place.

## What if "longest street name" actually meant something totally different?

![](/assets/images/2025-03-30-longest-street-name/hutz.png){:style="width: 100%; display:block; margin-left:auto; margin-right:auto"}

Let's take one last detour where words don't mean what we normally understand them to mean, and "longest street name" actually means something closer to "longest street, name". Or rather, "what's the longest stretch of road that has the same name"?

This is not going to be as thorough as it possibly could be, since, for instance, "Clairmont Road" mentioned above is also sometimes called "Clairmont Road Northeast". I'm just testing for strict name equality.

![](/assets/images/2025-03-30-longest-street-name/atlanta-streets.png){:style="width: 100%; display:block; margin-left:auto; margin-right:auto"}
<figcaption>Section of Atlanta roads, colored by street name. You can see the Briarcliff Rd./Moreland Ave. name change on the north-south road at the black arrow
</figcaption>

This is also a last-minute idea I had for this blog post that ended up being the hardest to calculate. Oh well. Let's take a look at our winners.

![](/assets/images/2025-03-30-longest-street-name/snoman.png){:style="display:block; margin-left:auto; margin-right:auto"}

1. 👑 First place, at 11,048 km, is the [Snoman Trail](https://overpass-turbo.eu/s/21yK){:target="_blank"} in Manitoba, a network of snowmobile trails that all happened to be named "Snoman Trail".

    This is an unexpected result! This is something like going to your nearest big city and every road has the same name. Oh you're looking for the Greek restaurant? Go 3 blocks this way down Main Street, turn left on Main Street, turn right the intersection of Main Street and Main Street, and then left again on Main Street.

    This is probably not what any of us thinks of when we think of a street or road, but is a fun result nonetheless.

![](/assets/images/2025-03-30-longest-street-name/great-northern.jpg){:style="width: 100%; display:block; margin-left:auto; margin-right:auto"}
<figcaption>Great Northern Highway (<a href="https://www.flickr.com/photos/huskyte/">Michael Theis</a>)
</figcaption>

2. 🏆 Second place, at 3,989 km, is western Australia's [Great Nothern Highway](https://www.openstreetmap.org/relation/6892208){:target="_blank"}.

    Turns out that our friends at dangerousroads.org already have a page [about this one](https://www.dangerousroads.org/australia-and-oceania/australia/8905-great-northern-highway.html){:target="_blank"}, wherein it's described as "the longest and most remote paved road in the world". Could have saved me some time had I just looked this up!

![](/assets/images/2025-03-30-longest-street-name/amur.jpg){:style="width: 100%; display:block; margin-left:auto; margin-right:auto"}
<figcaption>Amur Highway (<a href="https://commons.wikimedia.org/w/index.php?curid=92145513">Oleg Bor - Own work, CC BY-SA 4.0</a>)
</figcaption>
3. 🏅 Third place, at 3,758 km, is the [Amur Highway](https://www.openstreetmap.org/relation/16123741), running along the Russia-China border in eastern Russia.

    This is part of the larger Trans-Siberian highway, and according to [Wikipedia](https://en.wikipedia.org/wiki/R297_highway), up until about 2010, it had "massive marshes, gravel, rock, mud, sand, washboarding, potholes, stream fording, and detours along the elusive highway, with a noticeable absence of pavement". It has since been upgraded into "a dependable, modern farm road, but not the Autobahn."

![](/assets/images/2025-03-30-longest-street-name/phahonyotin.jpg){:style="width: 100%; display:block; margin-left:auto; margin-right:auto"}
<figcaption>Phahonyotin Road (<a href="https://commons.wikimedia.org/wiki/File:Phahonyothin_Road,_north_of_Ha_Yaek_Lat_Phrao_station.jpg">Wikipedia</a>)
</figcaption>

4. 🕺 Bonus fourth place, at 3,224 km, is [Phahonyothin Road](https://www.openstreetmap.org/relation/228025){:target="_blank"} in Thailand.

    I just thought this was interesting because we don't see a lot from southeast Asia on Wandrer!

Also it should be noted that the lengths here are way higher than the official lengths. The Great Northern Highway is ~3,200 km, while my measurements had it at almost 4,000 km. This is most likely the result of the highway being split in to multiple ways on OSM (say, a northbound way and a separate southbound way) that result in double counting in places.

## In the end

I didn't really expect that there might be 4 different ways to calculate "longest street name", and I'd love to come up with a fifth one somehow.

In the meantime, I know I said I didn't want to get into Team Cody versus Team Woodrow, but at the end of the day I think I'm Team Cody and that the _[Private First Class Cody Montana Carver, U.S. Army 3rd Infantry Division Memorial Bridge](https://www.openstreetmap.org/way/165226334){:target="_blank"}_ is the longest deliberately named road in the world.

Woodrow T. Cox's road has some technicalities around the true length of its name, and if we're considering external factors, Cody's bridge is _250 feet / 75 meters long_. You could bike across it in a single breath. I think there's something poetic about the longest street name in the world belonging to such a small section of road.
