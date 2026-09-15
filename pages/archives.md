---
layout: page
title: Archives
---

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
