---
layout: page
title: research
permalink: /research/
description: #A growing collection of your cool projects.
nav: true
nav_order: 3
display_categories: #[work, fun]
horizontal: false
---

<!-- pages/research.md -->
<div class="events">
{% if site.enable_research_categories and page.display_categories %}
  <!-- Display categorized projects -->
  {% for category in page.display_categories %}
  <a id="{{ category }}" href=".#{{ category }}">
    <h2 class="category">{{ category }}</h2>
  </a>
  {% assign categorized_research = site.research | where: "category", category %}
  {% assign sorted_research = categorized_research | sort %}

  <!-- Generate cards for each project -->
  {% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-2">
    {% for research in sorted_research %}
      {% include research_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="grid">
    {% for research in sorted_research %}
      {% include research.liquid %}
    {% endfor %}
  </div>
  {% endif %}
  {% endfor %}

{% else %}

  <!-- Display projects without categories -->

  {% assign sorted_research = site.research | sort %}

  <!-- Generate cards for each project -->
  {% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-2">
    {% for research in sorted_research %}
      {% include research_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="grid">
    {% for research in sorted_research %}
      {% include research.liquid %}
    {% endfor %}
  </div>
  {% endif %}
{% endif %}
</div>