---
layout: page
permalink: /platforms/
title: platforms
#description: digital platforms managed of DAIH
nav: true
nav_order: 5
---

Over the years, we have supported the development of various digital platforms for the Department of Foreign Languages and Literatures at the University of Verona, and we continue to oversee their maintenance. 

{% assign data = site.data.platforms %}

{% if data %}
  {% for group_name in data %}
    {% assign platformsType = group_name[1] %}
<h2 id="{{ group_name[0] }}" class="group">{{ group_name[0] }}</h2>
<ul>
    {% assign platforms = platformsType %}
    {% for platform in platforms %}
    <li>
        {% if platform.website %}<a href="{{ platform.website }}">{% endif %}
        {{ platform.name }}
        {% if platform.website %}</a>{% endif %}<br/>
        {{ platform.description }}
    </li>
    {% endfor %}
</ul>
  {% endfor %}
{% else %}
  <p>No platform data found.</p>
{% endif %}