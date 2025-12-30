---
layout: default
title: Artigos
lang: pt
---

## Todos os artigos

<div class="grid">
{% assign pt_posts = site.posts | where: "lang", "pt" %}
{% for post in pt_posts %}
  <div class="card">
    {% if post.cover %}
      {% if post.title contains "projetos backend" %}
        <img class="small" src="{{ post.cover }}" alt="">
      {% else %}
        <img class="round" src="{{ post.cover }}" alt="">
      {% endif %}
    {% endif %}
    <h3><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
    <div class="post-meta">{{ post.date | date: "%d/%m/%Y" }}</div>
    {% if post.excerpt %}<p>{{ post.excerpt | strip_html | truncate: 160 }}</p>{% endif %}
  </div>
{% endfor %}
</div>

{% if pt_posts.size == 0 %}
<p>Nenhum artigo encontrado em português.</p>
{% endif %}