---
layout: page
title: people
permalink: /people/
description: SOMETHING HERE! 
nav: true
nav_order: 2
display_categories: [current, former]
horizontal: true
---




<!-- pages/people.md -->
<div class="people">
{%- if site.enable_people_categories and page.display_categories %}
  <!-- Display categorized people -->
  {%- for category in page.display_categories  %}
  <h2 class="category">{{ category | upcase }}</h2>
  {%- assign categorized_people = site.people | where: "category", category -%}
  {%- assign sorted_people = categorized_people | sort: "name" %}

<!-- Generate cards for each person -->
{% if page.horizontal -%}
  <div class="container">
    <div class="row row-cols-2">
    {%- for person in sorted_people -%}
      {% include people_horizontal.html %}
    {%- endfor %}
    </div>
  </div>
  {%- else -%}
  <div class="grid">
    {%- for person in sorted_people -%}
      {% include person.html %}
    {%- endfor %}
  </div>
  {%- endif -%}
   <br/>   <br/>
  {% endfor %}

{%- else -%}
<!-- Display people without categories -->
{%- assign sorted_people = site.people | sort: "name" -%}

  <!-- Generate cards for each person -->
{% if page.horizontal -%}
  <div class="container">
    <div class="row row-cols-2">
    {%- for person in sorted_people -%}
      {% include people_horizontal.html %}
    {%- endfor %}
    </div>
  </div>
  {%- else -%}
  <div class="grid">
    {%- for person in sorted_people -%}
      {% include person.html %}
    {%- endfor %}
  </div>
  {%- endif -%}
{%- endif -%}
</div>
