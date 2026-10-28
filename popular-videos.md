---
layout: page
title: Pocha (@iitianbiker) - content creator
description: A reasonably new content creator with fairly engaging videos on YouTube and Instagram.
permalink: /popular-videos/
---

I am a reasonably new content creator, but my content has been fairly engaging (see the charts below). My overall following numbers are small, but I have become pretty good at content creation of late, especially with product promo videos. Check out my Insta reel of a [Shimoga homestay](https://www.instagram.com/iitianbiker/reel/DYIFpx_TWm3/), for instance.

## Views per subscriber comparison

**Views per subscriber** is a video's views divided by the channel's subscribers. It shows how well a creator's content reaches people compared to the size of their following, so a small channel can be compared with a big one. Below, I compare myself with other Indian travel motovloggers, using each creator's 10 latest travel uploads, long videos and Shorts separately.

{% assign people = site.data.creator_comparison %}
<div class="engagement">
  {% assign formats = "long,shorts" | split: "," %}
  {% for fmt in formats %}
    {% if fmt == "long" %}{% assign rows = people | where_exp: "c", "c.long" | sort: "long" | reverse %}{% assign label = "Long videos" %}
    {% else %}{% assign rows = people | where_exp: "c", "c.shorts" | sort: "shorts" | reverse %}{% assign label = "Shorts" %}{% endif %}
    {% if fmt == "long" %}{% assign max = rows.first.long | times: 1.0 %}{% else %}{% assign max = rows.first.shorts | times: 1.0 %}{% endif %}
    <div class="chart">
      <div class="chart-label">{{ label }}</div>
      {% for c in rows %}
        {% if fmt == "long" %}{% assign val = c.long %}{% else %}{% assign val = c.shorts %}{% endif %}
        {% assign w = val | times: 1.0 | divided_by: max | times: 100 | round: 1 %}
        <div class="chart-row{% if c.me %} chart-row-me{% endif %}" style="--hue: {{ w | times: 1.2 | round }}">
          <a class="chart-who" href="https://www.youtube.com/@{{ c.handle }}" target="_blank" rel="noopener">
            <img src="{{ '/assets/img/creators/' | append: c.handle | append: '.jpg' | relative_url }}" alt="" loading="lazy">
            <span>{% if c.me %}Me (Pocha){% else %}{{ c.name }}{% endif %}</span>
          </a>
          <div class="chart-track"><div class="chart-bar" style="width: {{ w }}%"></div></div>
          <span class="chart-value">{{ val }}×</span>
        </div>
      {% endfor %}
    </div>
  {% endfor %}

  <p class="engagement-note">Each value is the average over the creator's 10 latest travel uploads in that format
  (long videos from the last month are left out, since they haven't finished collecting views). Views are lifetime totals as of Oct 2026.
  Viral hits move these averages a lot, and the other channels are far larger than mine, so ratios naturally drop as channels grow.
  Bar colour runs from red (smallest) to green (longest) within each chart. Deepranjan Sachan has no Shorts. Instagram isn't included because view counts aren't public.</p>
</div>

## Popular Videos

My most-watched videos and shorts. YouTube entries have 1K+ views; Instagram doesn't expose view counts publicly, so reels show likes.

<div class="video-cards">
{% for v in site.data.popular_videos %}
  <a class="video-card{% if v.kind == 'Video' %} video-card-long{% endif %}" href="{{ v.url }}" target="_blank" rel="noopener">
    <div class="video-card-thumb"><img src="{{ v.thumb | relative_url }}" alt="" loading="lazy"></div>
    <div class="video-card-title">{{ v.title | escape }}</div>
    <div class="video-card-meta">
      {% if v.views %}<span>{{ v.views | divided_by: 1000.0 | round: 1 }}K views</span>{% else %}<span>{{ v.likes }} likes</span>{% endif %}
      {% include provider-icon.html source=v.source %}
    </div>
  </a>
{% endfor %}
</div>
