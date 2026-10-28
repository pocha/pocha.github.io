---
layout: page
title: 2026 Winter Ride (proposal)
description: Three candidate routes for my 2026 winter motorcycle ride, proposal to brands for collaboration.
permalink: /2026-winter-ride/
image: /images/altai-pic.jpg
---

<figure class="opening-photo">
  <img src="{{ '/images/altai-pic.jpg' | relative_url }}" alt="Ashish with his red adventure motorcycle on a road in front of a forested hill under a clear blue sky">
  <figcaption>Somewhere in the Altai region of Russia, on the way to Mongolia, 2024</figcaption>
</figure>

Below are 3 suggested routes that I am planning to ride a motorbike on. I will pick one depending on collaborating brand(s) preferences.

- **Brands I am looking for:** travel partner (bike provider), stay partner (hostels on the route) and food partner (restaurants on the route), whom I can cover in my vlogs.
- **Content cadence:** 1 reel every 2 day on the road (realtime) and 1 long-form video for every 7 days on the road. 
- **What I can offer:** a dedicated reel/short for your channel once a week of my journey, coverage in long-form videos. For stay partners, can do a drone shot of the establishment if it make sense. Check my [drone video of a homestay in Shimoga next to Tunga river](https://www.instagram.com/iitianbiker/reel/DYIFpx_TWm3/)
- **What I am looking for:** brands with a social media presence who are open to be reel collaborator (special preference to the ones that would like to run a story about my ride on their newsletter), willing to offer support in cash, kind or both. Can also offer explicit mention in long form videos ("video sponsored by xxx") in lieu of cash support.

Quick peek of my content creation skills: [My journey as content creator]({{ '/popular-videos/' | relative_url }}).

{% for r in site.data.winter_routes %}
{% assign km_round = r.km | divided_by: 100 | times: 100 %}
{% if km_round >= 1000 %}{% capture km_text %}{{ km_round | divided_by: 1000 }},{{ km_round | modulo: 1000 | prepend: "000" | slice: -3, 3 }}{% endcapture %}{% else %}{% assign km_text = km_round %}{% endif %}
## {{ forloop.index }}. {{ r.title }}: {% if r.days %}{{ r.days }} days, {% endif %}~{{ km_text }} km

{{ r.description }}
{% unless r.itinerary %}
**{{ r.stops }} stops** &middot; starts and ends in Delhi

{% if r.trek %}**On foot:** {{ r.trek }}

{% endif %}{% if r.note %}<p class="route-note">{{ r.note }}</p>

{% endif %}{% endunless %}
<div class="route-map" data-src="{{ '/assets/data/routes/' | append: r.key | append: '.json' | relative_url }}" data-color="{{ r.color }}"></div>

{% if r.itinerary %}
<details class="route-stops">
  <summary>Day-by-day plan</summary>
<ul class="itinerary-list">
  {% for d in r.itinerary %}
  <li><strong>Day {{ d.day }}</strong> &ndash; {{ d.route }}{% if d.km > 0 %} ({{ d.km }} km{% if d.trek_km %} ride + {{ d.trek_km }} km trek{% endif %}){% endif %}{% if d.type == "shoot" and d.km == 0 %} (rest &amp; content day){% endif %} &ndash; {{ d.see }}</li>
  {% endfor %}
</ul>
</details>
{% else %}
<details class="route-stops">
  <summary>Stops in order</summary>
  <ol start="0">
    {% for s in r.stop_names %}<li>{{ s }}</li>{% endfor %}
  </ol>
</details>
{% endif %}
{% endfor %}

## What I am looking for

- **Travel / bike partner:** an ADV bike (preferably Xpulse) with your brand decals, and soft side pannier bags, 35 L each.
- **Stay partner:** a stay at your establishments on the way, with 2 meals. Open to altering route a bit to cover more establishments.
  - **Zostel:** on the Uttarakhand circuit, your properties at Rishikesh, Mussoorie, Mukteshwar and Nainital overlap with my route. In Rajasthan: Jaisalmer, Sam Desert, Jodhpur, Udaipur, Bundi, Pushkar and Jaipur.
  - **The Hosteller:** on the Uttarakhand circuit: Rishikesh, Dehradun, Chakrata, Mussoorie, Kasar Devi (a short detour from Almora) and Nainital. In Rajasthan: Jodhpur, Udaipur and Jaipur.
  - **GoStops:** on the Uttarakhand circuit: Rishikesh, Mussoorie and Nainital. In Rajasthan: Udaipur and Jaipur.
- **Content partner:** help with reel editing and full-form video editing, specially around effects, animations & map rendering. Reel editing is more important as I intend to create one reel per day on the road & brand specific reels once a week. In return, you get your brand watermark on the videos (except the brand reels) and mention with link in the description of long form videos.
- **Gear partner:** I will showcase your product with the brand name visible. Gear I can put to use: camera mounts, riding gear and warm clothing. Gears I already have - Dji action cam, insta360, Potesic drone, Dji mic mini. 

All partners get brand attribution in the description of the long-form videos.

<p class="route-note">Routes are drawn on real roads and are indicative; the final route may change with weather and road closures. Map data &copy; OpenStreetMap contributors.</p>
