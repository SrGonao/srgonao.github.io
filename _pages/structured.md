---
layout: default
permalink: /blog
title: structured
nav: true
nav_order: 1
nav_name: blog
pagination:
  enabled: true
  collection: posts
  sort_field: date
  sort_reverse: true
  per_page: 5
  permalink: /blog/page/:num/
---

<div class="post">
  <div class="header-bar">
    <h1>{{ site.blog_name }}</h1>
    <h2>{{ site.blog_description }}</h2>
  </div>

  <ul class="post-list">
    {% if site.posts.size > 0 %}
      {% for post in paginator.documents %}
        <li>
          <h3><a class="post-title" href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
          <p class="post-meta">{{ post.date | date: '%B %d, %Y' }}</p>
          {{ post.content }}
        </li>
      {% endfor %}
    {% else %}
      <li><p>No blog posts yet.</p></li>
    {% endif %}
  </ul>

  {% if paginator.total_pages > 1 %}
    {% include pagination.liquid %}
  {% endif %}
</div>
