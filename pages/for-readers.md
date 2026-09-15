---
layout: page
title: For Readers
permalink: /for-readers/
---

## Author Interviews

<ul>
{% assign posts = site.categories.author-interview %}
{% for post in posts %}
  <li><a href="{{ post.url }}">{{ post.title }}</a></li>
{% endfor %}
</ul>

## Book Reviews

<ul>
{% assign posts = site.categories.book-review %}
{% for post in posts %}
  <li><a href="{{ post.url }}">{{ post.title }}</a></li>
{% endfor %}
</ul>
