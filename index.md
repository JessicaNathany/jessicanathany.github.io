---
layout: default
title: "Início"
---

<div class="home-intro">
  <img src="/assets/img/perfil.jpg" alt="Foto Jéssica" class="profile-pic">
  <h1>Bem-vindos ao meu blog!</h1>
  <p>Sou Jéssica, desenvolvedora de software e fundadora do Café Debug ☕. Aqui compartilho artigos sobre tecnologia, projetos e ideias.</p>
</div>

<nav class="menu">
  <ul>
    <li><a href="/artigos">Artigos</a></li>
    <li><a href="/projetos">Projetos</a></li>
    <li><a href="/podcast">Podcast</a></li>
    <li><a href="/quem-sou">Quem sou</a></li>
  </ul>
</nav>

### Últimos artigos

{% assign posts = site.posts | limit: 6 %}
{% if posts.size > 0 %}
<div class="grid">
{% for post in posts %}
  <div class="card">
    {% if post.cover %}
      <img class="round" src="{{ post.cover }}" alt="Capa do post">
    {% endif %}
    <h3><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
    <div class="post-meta">{{ post.date | date: "%d/%m/%Y" }}</div>
    {% if post.excerpt %}
      <p>{{ post.excerpt | strip_html | truncate: 140 }}</p>
    {% endif %}
  </div>
{% endfor %}
</div>
{% else %}
<p>Em breve, novos artigos sobre tecnologia e desenvolvimento!</p>
{% endif %}



