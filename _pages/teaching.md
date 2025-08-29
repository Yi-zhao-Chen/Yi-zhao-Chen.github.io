---
layout: page
permalink: /teaching/
title: Teaching
description: The following are the courses which I taught or in which I served as a teaching assistant.
nav: true
nav_order: 3
display_categories:
horizontal: true
---
<!-- 基本照抄project.md，唯一的差别是将collection中元素的排序顺序调整了一下，此外在config.yml中添加了enable_teaching_categories -->

<div class="teaching">
{% if site.enable_teaching_categories and page.display_categories %}
  <!-- Display categorized classes -->
  {% for category in page.display_categories %}
  <a id="{{ category }}" href=".#{{ category }}">
    <h2 class="category">{{ category }}</h2>
  </a>
  {% assign categorized_teaching = site.teaching | where: "category", category %}
  {% assign sorted_courses = categorized_teaching | sort: "date" | reverse %}
  <!-- Generate cards for each class -->
  {% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for course in sorted_courses %}
      {% include projects_horizontal.liquid %}
      <!-- !先试试projects_horizontal.liquid能不能用(下面一行也用了一次) -->
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for course in sorted_courses %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
  {% endif %}
  {% endfor %}

{% else %}

<!-- Display projects without categories -->

{% assign sorted_courses = site.teaching | sort: "date" | reverse %}

<!-- Generate cards for each project -->

{% if page.horizontal %}

<div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for course in sorted_courses %}
      {% include projects_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for course in sorted_courses %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
  {% endif %}
{% endif %}
</div>
