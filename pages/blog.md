---
layout: page
title: Blog
---

{% for post in paginator.posts %}
  <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
  <p>{{ post.date | date: "%Y-%m-%d" }}</p>
{% endfor %}

{% include pagination.html %}
