---
layout: page
title: network
permalink: /network/
description: #A growing collection of your cool collaborations.
nav: true
nav_order: 4
display_categories: #[work, fun]
horizontal: false
---

<!-- pages/collaborations.md -->
<div class="events">
{% if site.enable_collaboration_categories and page.display_categories %}
  <!-- Display categorized collaborations -->
  {% for category in page.display_categories %}
  <a id="{{ category }}" href=".#{{ category }}">
    <h2 class="category">{{ category }}</h2>
  </a>
  {% assign categorized_collaborations = site.collaborations | where: "category", category %}
  {% assign sorted_collaborations = categorized_collaborations | sort: "importance" %}
  <!-- Generate cards for each collaboration -->
  {% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-2">
    {% for collaboration in sorted_collaborations %}
      {% include collaboration_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="grid">
    {% for collaboration in sorted_collaborations %}
      {% include collaboration.liquid %}
    {% endfor %}
  </div>
  {% endif %}
  {% endfor %}

{% else %}

  <!-- Display collaborations without categories -->

  {% assign sorted_collaborations = site.collaborations | sort: "importance" %}

  <!-- Generate cards for each collaboration -->

  {% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-2">
    {% for collaboration in sorted_collaborations %}
      {% include collaboration_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="grid">
    {% for collaboration in sorted_collaborations %}
      {% include collaboration.liquid %}
    {% endfor %}
  </div>
  {% endif %}
{% endif %}
</div>
