---
layout: page
title: My Books
---

<ul>
{% for book in site.books %}
  <li><a href="{{ book.url }}">{{ book.title }}</a></li>
{% endfor %}
</ul>
