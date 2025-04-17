---
layout: page
permalink: /people/
title: people
#description: members of DAIH
nav: true
nav_rank: 2
---

{% assign data = site.data.members %}

{% if data %}
  {% for group_name in data %}
    {% assign members = group_name[1] %}
<h2 id="{{ group_name[0] }}" class="group">{{ group_name[0] }}</h2>
<ul>
    {% assign sorted_members = members | sort: "surname" %}
    {% for member in sorted_members %}
    <li>
        {% if member.website %}<a href="{{ member.website }}">{% endif %}
        {{ member.name }} {{ member.surname }}
        {% if member.website %}</a>{% endif %} {% if member.period %}({{ member.period }}){% endif %}
        <!-- {% if member.position %}<br/>{{ member.position }}{% endif %} -->
        {% if member.affiliation %}<br/>{{ member.affiliation }}{% endif %}
    </li>
    {% endfor %}
</ul>
  {% endfor %}
{% else %}
  <p>No member data found.</p>
{% endif %}
