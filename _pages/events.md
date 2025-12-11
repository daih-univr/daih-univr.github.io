---
layout: page
title: initiatives
permalink: /events/
description: #A growing collection of your cool projects.
nav: true
nav_order: 4
display_categories: [conferences, workshops, seminars, teaching & training]
horizontal: false
---

DAIH contributes to the organization of a wide range of initiatives, including conferences, workshops, seminars, public events, and training activities.

<!-- pages/events.md -->
<div class="events">
{% if site.enable_event_categories and page.display_categories %}
  <!-- Display categorized projects -->
  {% for category in page.display_categories %}
  <a id="{{ category }}" href=".#{{ category }}">
    <h2 class="category">{{ category }}</h2>
  </a>
  {% assign categorized_events = site.events | where: "category", category %}
  {% assign sorted_events = categorized_events | sort %}

  <!-- Generate cards for each project -->
  {% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-2">
    {% for event in sorted_events %}
      {% include events_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="grid">
    {% for event in sorted_events %}
      {% include events.liquid %}
    {% endfor %}
  </div>
  {% endif %}
  {% endfor %}

{% else %}

  <!-- Display projects without categories -->

  {% assign sorted_events = site.events | sort: "dates" %}

  <!-- Generate cards for each project -->
  {% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-2">
    {% for event in sorted_events %}
      {% include events_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="grid">
    {% for event in sorted_events %}
      {% include events.liquid %}
    {% endfor %}
  </div>
  {% endif %}
{% endif %}
</div>
