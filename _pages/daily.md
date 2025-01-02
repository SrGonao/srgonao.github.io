---
layout: default
permalink: /daily
title: daily
nav: true
nav_order: 2
nav_name: daily
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

<p>Debug daily:</p>
<pre>
Site daily posts: {{ site.daily | size }}
Paginator posts: {{ paginator.posts | size }}
</pre>

<div class="post">
  <div class="header-bar">
    <h1>Research Journal</h1>
    <h2>Daily updates on my research. Posts may be incoherent and wrong.</h2>
  </div>

  <ul class="post-list">
    {% assign daily_posts = site.daily | sort: 'date' | reverse %}
    {% for post in daily_posts %}
      <li>
        <h3>
          <a class="post-title" href="{{ post.url | relative_url }}">{{ post.title }}</a>
        </h3>
        <p class="post-meta">
          {{ post.date | date: '%B %d, %Y' }}
        </p>
        {{ post.content }}
      </li>
    {% endfor %}
  </ul>

  {% if paginator.total_pages > 1 %}
    {% include pagination.liquid %}
  {% endif %}
</div>

