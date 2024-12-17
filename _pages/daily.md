---
layout: default
permalink: /daily/
title: daily
nav: true
nav_name: daily      # This will show in the navigation bar
nav_order: 2
pagination:
  enabled: true
  collection: daily
  permalink: /daily/page/:num/
  per_page: 5
  sort_field: date
  sort_reverse: true
  trail:
    before: 1
    after: 3
---


<div class="post">
  <div class="header-bar">
    <h1>Daily Posts</h1>
    <h2>Quick thoughts and daily updates</h2>
  </div>

  <ul class="post-list">
    {% raw %}{% for post in paginator.documents %}
      <li>
        <h3>
          <a class="post-title" href="{{ post.url | relative_url }}">{{ post.title }}</a>
        </h3>
        <p class="post-meta">
          {{ post.date | date: '%B %d, %Y' }}
        </p>
        {{ post.content }}
      </li>
    {% endfor %}{% endraw %}
  </ul>

  {% raw %}{% if page.pagination.enabled %}
    {% include pagination.liquid %}
  {% endif %}{% endraw %}
</div>