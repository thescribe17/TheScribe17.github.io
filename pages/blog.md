---
layout: page
title: Blog
permalink: /blog/
---

{% for post in paginator.posts %}
  <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
  <p>{{ post.date | date: "%Y-%m-%d" }}</p>
{% endfor %}

{% include pagination.html %}
