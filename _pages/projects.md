---
layout: page
title: research
permalink: /projects/
description: research projects or other things I'm working on.
nav: true
nav_order: 1
display_categories: [Publications, Working Papers] # Will add more here as time progresses!
horizontal: false
---

<!-- pages/projects.md -->
<div class="projects">
{% assign all_projects = "" | split: "" %}

{% if site.enable_project_categories and page.display_categories %}
  <!-- Display categorized projects -->
  {% for category in page.display_categories %}
  <a id="{{ category }}" href=".#{{ category }}">
    <h2 class="category">{{ category }}</h2>
  </a>

  {% assign categorized_projects = site.projects | where: "category", category %}
  {% assign sorted_projects = categorized_projects | where_exp: "item", "item.hidden != true" | sort: "importance" %}

  {%- assign all_projects = all_projects | concat: sorted_projects -%}

  <!-- Generate cards for each project -->
  {% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for project in sorted_projects %}
      {% include projects_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_projects %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
  {% endif %}
  {% endfor %}

{% else %}

<!-- Display projects without categories -->
{% assign sorted_projects = site.projects | where_exp: "item", "item.hidden != true" | sort: "importance" %}
{%- assign all_projects = sorted_projects -%}

<!-- Generate cards for each project -->
{% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for project in sorted_projects %}
      {% include projects_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
{% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_projects %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
{% endif %}
{% endif %}
</div>

<!-- ✅ MODALS RENDERED OUTSIDE THE GRID -->
{% for project in all_projects %}
{% if project.abstract %}
<div class="modal fade" id="abs-{{ project.title | slugify }}" tabindex="-1" role="dialog" aria-hidden="true">
  <div class="modal-dialog modal-lg modal-dialog-centered" role="document">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title">{{ project.title }}</h5>
        <button type="button" class="close" data-dismiss="modal" aria-label="Close">
          <span aria-hidden="true">&times;</span>
        </button>
      </div>

      <div class="modal-body">
        {{ project.abstract | markdownify }}
      </div>

      <div class="modal-footer">
        {% if project.pdf %}
        <a class="btn btn-sm z-depth-0" href="{{ project.pdf | relative_url }}">PDF</a>
        {% endif %}
        {% if project.doi %}
        <a class="btn btn-sm z-depth-0" href="https://doi.org/{{ project.doi }}" target="_blank" rel="noopener">DOI</a>
        {% endif %}
        <button type="button" class="btn btn-sm z-depth-0" data-dismiss="modal">Close</button>
      </div>
    </div>
  </div>
</div>
{% endif %}
{% endfor %}
