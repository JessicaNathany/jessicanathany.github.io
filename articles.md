---
layout: default
title: Articles
lang: en
---

## All articles

<div class="grid">
{% assign en_posts = site.posts | where: "lang", "en" %}
{% for post in en_posts %}
  <div class="card">
    {% if post.cover %}
      <img class="round" src="{{ post.cover }}" alt="">
    {% endif %}
    <h3><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
    <div class="post-meta">{{ post.date | date: "%m/%d/%Y" }}</div>
    {% if post.excerpt %}<p>{{ post.excerpt | strip_html | truncate: 160 }}</p>{% endif %}
  </div>
{% endfor %}
</div>

{% if en_posts.size == 0 %}
<p>No articles found in English.</p>
{% endif %}