---
layout: page
title: tools
permalink: /tools/
description: Software for researchers, learners, and anyone who reads more than they remember.
nav: true
nav_order: 4
display_categories: [Reading & Memory, For Researchers]
horizontal: false
---

I build small, focused tools when the existing ones don't do what I need. Everything here is open-source unless noted.

<!-- pages/tools.md -->
<div class="projects">
{% if site.enable_project_categories and page.display_categories %}
  {% for category in page.display_categories %}
  {% assign categorized_tools = site.tools | where: "category", category %}
  {% assign sorted_tools = categorized_tools | where_exp: "item", "item.hidden != true" | sort: "importance" %}
  {% if sorted_tools.size > 0 %}
  <a id="{{ category }}" href=".#{{ category }}">
    <h2 class="category">{{ category }}</h2>
  </a>

  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_tools %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
  {% endif %}
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
