---
layout: default
title: Artigos
---

## Todos os artigos

<div class="grid">
{% for post in site.posts %}
  <div class="card">
    {% if post.cover %}
      <img class="round" src="{{ post.cover }}" alt="">
    {% endif %}
    <h3><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
    <div class="post-meta">{{ post.date | date: "%d/%m/%Y" }}</div>
    {% if post.excerpt %}<p>{{ post.excerpt | strip_html | truncate: 160 }}</p>{% endif %}
  </div>
{% endfor %}
</div>