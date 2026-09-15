---
layout: page
title: Archives
permalink: /archives/
subtitle: What will you find?
---

## Tag Cloud

<div class="tag-cloud">
  {% assign tags = site.tags %}
  {% for tag in tags %}
    {% assign count = tag[1].size %}
    <a href="{{ '/tag/' | append: tag[0] | relative_url }}"
       class="tag-item"
       style="font-size: {{ 0.8 | plus: count | times: 0.2 }}rem;">
      {{ tag[0] }} ({{ count }})
    </a>
  {% endfor %}
</div>

## By Year

{% assign years = site.posts | group_by_exp: "post", "post.date | date: '%Y'" %}
{% for year in years %}
  <h2>{{ year.name }}</h2>
  <ul>
  {% for post in year.items %}
    <li><a href="{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
  </ul>
{% endfor %}
