---
layout: page
title: Archives
permalink: /archives/
subtitle: What will you find?
---

## Search Posts

<input type="text" id="search-input" placeholder="Search posts..." />

<ul id="search-results"></ul>

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

<script>
  // Build a list of posts for searching
  const posts = [
    {% for post in site.posts %}
      {
        "title": "{{ post.title | escape }}",
        "url": "{{ post.url | relative_url }}",
        "content": "{{ post.content | strip_html | escape }}",
        "date": "{{ post.date | date: '%-d %B %Y' }}"
      },
    {% endfor %}
  ];

  const input = document.getElementById('search-input');
  const results = document.getElementById('search-results');

  input.addEventListener('input', function() {
    const query = this.value.toLowerCase();
    results.innerHTML = "";

    if (query.length < 2) return; // avoid noise

    const matches = posts.filter(post =>
      post.title.toLowerCase().includes(query) ||
      post.content.toLowerCase().includes(query)
    );

    matches.forEach(post => {
      const li = document.createElement('li');
      li.innerHTML = `<a href="${post.url}">${post.title}</a> — ${post.date}`;
      results.appendChild(li);
    });
  });
</script>

