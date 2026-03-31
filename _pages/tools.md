---
layout: page
title: tools
permalink: /tools/
description: Tools and extensions I've built.
nav: true
nav_order: 3
display_categories: [Anki Tools]
horizontal: false
---

<!-- pages/tools.md -->
<div class="projects">
{% if site.enable_project_categories and page.display_categories %}
  {% for category in page.display_categories %}
  <a id="{{ category }}" href=".#{{ category }}">
    <h2 class="category">{{ category }}</h2>
  </a>

{% assign categorized_tools = site.tools | where: "category", category %}
{% assign sorted_tools = categorized_tools | where_exp: "item", "item.hidden != true" | sort: "importance" %}

  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_tools %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
  {% endfor %}

{% else %}

{% assign sorted_tools = site.tools | where_exp: "item", "item.hidden != true" | sort: "importance" %}

  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_tools %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
{% endif %}
</div>
