---
layout: page
permalink: /outreach/
title: outreach
description: A page describing my outreach activity.
nav: false
nav_order: #
display_categories: #
horizontal: false
---

Here is a list of some outreach events I have organised or participated in. Hope you like them!


<!-- pages/outreach.md - use the same formatting as projects -->
<div class="projects">
{%- if site.enable_project_categories and page.display_categories %}
  <!-- Display categorized outreach -->
  {%- for category in page.display_categories %}
  <h2 class="category">{{ category }}</h2>
  {%- assign categorized_projects = site.outreach | where: "category", category -%}
  {%- assign sorted_projects = categorized_projects | sort: "year" %}
  <!-- Generate cards for each outreach event -->
  {% if page.horizontal -%}
  <div class="container">
    <div class="row row-cols-2">
    {%- for project in sorted_projects -%}
      {% include projects_horizontal.html %}
    {%- endfor %}
    </div>
  </div>
  {%- else -%}
  <div class="grid">
    {%- for project in sorted_projects -%}
      {% include projects.html %}
    {%- endfor %}
  </div>
  {%- endif -%}
  {% endfor %}

{%- else -%}
<!-- Display outreach without categories -->
  {%- assign sorted_projects = site.outreach | sort: "year" -%}
  <!-- Generate cards for each outreach event -->
  {% if page.horizontal -%}
  <div class="container">
    <div class="row row-cols-2">
    {%- for project in sorted_projects -%}
      {% include projects_horizontal.html %}
    {%- endfor %}
    </div>
  </div>
  {%- else -%}
  <div class="grid">
    {%- for project in sorted_projects -%}
      {% include projects.html %}
    {%- endfor %}
  </div>
  {%- endif -%}
{%- endif -%}
</div>
