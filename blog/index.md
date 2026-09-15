---
layout: page
title: Blog
subtitle: Updates, news, and writing reflections
permalink: /blog/
---

{% for post in paginator.posts %}
  <article class="blog-item">
    <h2><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h2>

    {% if post.subtitle %}
      <p class="blog-subtitle">{{ post.subtitle }}</p>
    {% endif %}

    <p class="blog-date">{{ post.date | date: "%-d %B %Y" }}</p>

    <p class="blog-excerpt">
      {{ post.excerpt | strip_html | truncate: 160 }}
    </p>

    <hr>
  </article>
{% endfor %}

<div class="pagination">
  {% if paginator.previous_page %}
    <a class="prev" href="{{ paginator.previous_page_path | relative_url }}">&laquo; Newer Posts</a>
  {% endif %}

  {% if paginator.next_page %}
    <a class="next" href="{{ paginator.next_page_path | relative_url }}">Older Posts &raquo;</a>
  {% endif %}
</div>
