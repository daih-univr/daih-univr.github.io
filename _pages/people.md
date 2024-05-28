---
layout: page
permalink: /people/
title: people
#description: members of DAIH
nav: true
nav_rank: 2
---

{% assign groups = site.members | sort: "group_rank" | map: "group" | uniq %}
{% for group in groups %}
<!-- ## {{ group }} -->
<h2 id="{{ group }}" class="group">{{ group }}</h2>


    {% assign members = site.members | sort: "profile.surname" | where: "group", group %}
<ul>
    {% for member in members %}
    <li>
        {% if member.profile.website %}<a href="{{ member.profile.website }}">{% endif %}
        {{ member.profile.name }} {{ member.profile.surname }}
        {% if member.profile.website %}</a>{% endif %}
        <!-- {% if member.profile.position %}<br/>{{ member.profile.position }}{% endif %} -->
        {% if member.profile.affiliation %}<br/>{{ member.profile.affiliation }}{% endif %}
    </li>
    {% endfor %}
</ul>
{% endfor %}