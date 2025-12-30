---
layout: default
title: "Home"
lang: en
---

<div class="home-intro">
  <img src="/assets/img/perfil.jpg" alt="Your photo" class="profile-pic">
  <h1>Welcome to my blog!</h1>
  <p>I'm Jéssica Nathany, developer and here I share knowledge about technology.</p>
</div>

<nav class="menu">
  <ul>
    <li><a href="/articles">Articles</a></li>
    <li><a href="/projects">Projects</a></li>
    <li><a href="/about">About</a></li>
  </ul>
</nav>

### Latest articles

{% assign posts = site.posts | where: "lang", "en" | limit: 6 %}
{% if posts.size > 0 %}
<div class="grid">
{% for post in posts %}
  <div class="card">
    {% if post.cover %}
      <img class="round" src="{{ post.cover }}" alt="Post cover">
    {% endif %}
    <h3><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
    <div class="post-meta">{{ post.date | date: "%m/%d/%Y" }}</div>
    {% if post.excerpt %}
      <p>{{ post.excerpt | strip_html | truncate: 140 }}</p>
    {% endif %}
  </div>
{% endfor %}
</div>
{% else %}
<p>Soon, new articles about technology!</p>
{% endif %}