---
layout: post

title: "Como criar um blog completo no GitHub Pages com Jekyll - Guia definitivo"

date: 2025-12-30

lang: pt

cover: "/assets/img/githubpages.png"

excerpt: "Guia completo passo a passo para criar seu próprio blog no GitHub Pages usando Jekyll, desde a configuração inicial até a publicação de artigos."

tags: [github-pages, jekyll, blog, tutorial]
---

## Introdução

Criar um blog técnico é uma excelente forma de compartilhar conhecimento e construir sua presença online como desenvolvedor. Neste guia completo, vou te mostrar como criar um blog profissional no GitHub Pages usando Jekyll, totalmente gratuito e com domínio personalizado.

## Por que GitHub Pages?

- **Gratuito** - Hospedagem sem custo
- **Integração Git** - Versionamento automático  
- **Jekyll integrado** - Gerador de sites estáticos
- **Domínio personalizado** - `seuusername.github.io`
- **HTTPS automático** - Segurança incluída
- **Deploy automático** - A cada push

##  Passo 1: Configuração inicial

### 1.1. Criando o repositório

1. **Acesse o GitHub** e crie um novo repositório
2. **Nome obrigatório**: `seuusername.github.io` (substitua pelo seu username)
3. **Marque como público** (obrigatório para contas gratuitas)
4. **Adicione um README.md** inicial

```bash
# Clone o repositório
git clone https://github.com/seuusername/seuusername.github.io.git

cd seuusername.github.io
```

### 1.2. Estrutura de pastas

Crie a seguinte estrutura:

```
seuusername.github.io/
├── _config.yml          # Configurações do Jekyll
├── _layouts/            # Templates do site
│   ├── default.html
│   └── post.html
├── _posts/              # Seus artigos
├── assets/              # CSS, imagens, JS
│   ├── css/
│   └── img/
├── index.md             # Página inicial
├── artigos.md           # Lista de artigos
├── quem-sou.md         # Sobre você
└── Gemfile              # Dependências Ruby
```

## Passo 2: Configurando o Jekyll

### 2.1. Arquivo `_config.yml`

```yaml
title: "Seu Nome"

description: "Seu blog sobre desenvolvimento e tecnologia"

author: "Seu Nome"

url: "https://seuusername.github.io"

baseurl: ""

markdown: kramdown

# Build settings
plugins:
  - jekyll-feed

# Navegação
nav:
  - label: "Quem sou"
    url: "/quem-sou"
  - label: "Artigos"
    url: "/artigos"
  - label: "Projetos"
    url: "/projetos"

# Permalinks
permalink: /artigos/:title/
```

### 2.2. Gemfile para dependências

```ruby
source "https://rubygems.org"

gem "jekyll", "~> 4.3.0"

gem "jekyll-feed", "~> 0.12"

gem "github-pages", group: :jekyll_plugins

# Windows compatibility
platforms :mingw, :x64_mingw, :mswin, :jruby do
  gem "tzinfo", ">= 1", "< 3"
  gem "tzinfo-data"
end

gem "wdm", "~> 0.1.1", :platforms => [:mingw, :x64_mingw, :mswin]
```

## Passo 3: Criando layouts

### 3.1. Layout principal (`_layouts/default.html`)

```html
<!DOCTYPE html>
<html lang="pt-br">
  <head>
    <meta charset="utf-8">
    <title>{{ page.title }} | {{ site.title }}</title>
    <meta name="description" content="{{ site.description }}">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <link rel="stylesheet" href="{{ '/assets/css/style.css' | relative_url }}">
  </head>
  <body>
    <header class="site-header">
      <div class="container">
        <div class="navbar">
          <a href="{{ '/' | relative_url }}" class="site-title">{{ site.title }}</a>
          {% for item in site.nav %}
            <a href="{{ item.url | relative_url }}">{{ item.label }}</a>
          {% endfor %}
        </div>
      </div>
    </header>

    <main class="container">
      {{ content }}
    </main>

    <footer class="container">
      <p>© {{ site.time | date: '%Y' }} {{ site.author }} — Hospedado no GitHub Pages</p>
    </footer>
  </body>
</html>
```

### 3.2. Layout para posts (`_layouts/post.html`)

```html
---
layout: default
---
<article class="post">
  <header class="post-header">
    <h1>{{ page.title }}</h1>
    <div class="post-meta">
       Publicado em {{ page.date | date: "%d/%m/%Y" }}
      {% if page.tags and page.tags.size > 0 %}
        <br> Tags: 
        {% for tag in page.tags %}
          <span class="tag">{{ tag }}</span>{% unless forloop.last %}, {% endunless %}
        {% endfor %}
      {% endif %}
    </div>
  </header>
  
  <div class="post-content">
    {{ content }}
  </div>
  
  <footer class="post-footer">
    <hr>
    <p><a href="/artigos">← Voltar para todos os artigos</a></p>
  </footer>
</article>
```

## Passo 4: Página inicial

### 4.1. Arquivo `index.md`

```markdown
---
layout: default

title: "Início"
---

<div class="home-intro">
  <img src="/assets/img/perfil.jpg" alt="Sua foto" class="profile-pic">
  <h1>Bem-vindos ao meu blog!</h1>
  <p>Sou [Seu Nome], desenvolvedor(a) e aqui compartilho conhecimentos sobre tecnologia.</p>
</div>

<nav class="menu">
  <ul>
    <li><a href="/artigos">Artigos</a></li>
    <li><a href="/projetos">Projetos</a></li>
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
<p>Em breve, novos artigos sobre tecnologia!</p>
{% endif %}
```

## Passo 5: Estilização CSS

### 5.1. Arquivo `assets/css/style.css`

```css
---
---

/* Estilos base */
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  line-height: 1.6;
  color: #333;
  background-color: #fff;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
}

/* Header */
.site-header {
  background-color: #2c3e50;
  color: white;
  padding: 1rem 0;
}

.navbar {
  display: flex;
  align-items: center;
  gap: 2rem;
}

.navbar a {
  color: white;
  text-decoration: none;
  font-weight: 500;
  transition: color 0.3s ease;
}

.navbar a:hover {
  color: #3498db;
}

.site-title {
  margin-right: auto !important;
  font-size: 1.2rem;
  font-weight: bold;
}

/* Home intro */
.home-intro {
  text-align: center;
  padding: 3rem 0;
}

.profile-pic {
  width: 200px;
  height: 200px;
  border-radius: 50%;
  margin-bottom: 1rem;
  object-fit: cover;
  border: 4px solid #3498db;
  box-shadow: 0 4px 15px rgba(0,0,0,0.2);
}

.home-intro h1 {
  font-size: 2.5rem;
  margin-bottom: 1rem;
  color: #2c3e50;
}

.home-intro p {
  font-size: 1.2rem;
  color: #666;
  max-width: 600px;
  margin: 0 auto;
}

/* Menu */
.menu {
  text-align: center;
  margin: 2rem 0;
}

.menu ul {
  list-style: none;
  display: flex;
  justify-content: center;
  gap: 2rem;
  flex-wrap: wrap;
}

.menu a {
  background-color: #3498db;
  color: white;
  padding: 0.75rem 1.5rem;
  text-decoration: none;
  border-radius: 5px;
  font-weight: 500;
  transition: background-color 0.3s ease;
}

.menu a:hover {
  background-color: #2980b9;
}

/* Grid */
.grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
  margin: 2rem 0;
}

/* Cards */
.card {
  background: white;
  border-radius: 8px;
  padding: 1.5rem;
  box-shadow: 0 2px 10px rgba(0,0,0,0.1);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.card:hover {
  transform: translateY(-5px);
  box-shadow: 0 5px 20px rgba(0,0,0,0.15);
}

.card h3 {
  color: #2c3e50;
  margin-bottom: 0.5rem;
  font-size: 1.25rem;
}

.card h3 a {
  color: inherit;
  text-decoration: none;
}

.card h3 a:hover {
  color: #3498db;
}

.post-meta {
  color: #999;
  font-size: 0.9rem;
  margin-bottom: 0.5rem;
}

/* Post styles */
.post {
  max-width: 800px;
  margin: 0 auto;
  padding: 2rem 0;
}

.post h1 {
  color: #2c3e50;
  margin-bottom: 1rem;
  font-size: 2.5rem;
}

.post-content {
  line-height: 1.8;
  color: #333;
}

.post-content h2 {
  color: #2c3e50;
  margin: 2rem 0 1rem 0;
  font-size: 1.8rem;
}

.post-content h3 {
  color: #2c3e50;
  margin: 1.5rem 0 0.5rem 0;
  font-size: 1.4rem;
}

.post-content code {
  background: #f8f9fa;
  padding: 0.2rem 0.4rem;
  border-radius: 3px;
  font-size: 0.9rem;
}

.post-content pre {
  background: #f8f9fa;
  border: 1px solid #e9ecef;
  border-radius: 4px;
  padding: 1rem;
  overflow-x: auto;
  margin-bottom: 1.5rem;
}

.tag {
  background: #3498db;
  color: white;
  padding: 0.2rem 0.5rem;
  border-radius: 3px;
  font-size: 0.8rem;
  margin-right: 0.5rem;
}

/* Responsive */
@media (max-width: 768px) {
  .home-intro h1 {
    font-size: 2rem;
  }
  
  .navbar {
    flex-direction: column;
    gap: 1rem;
  }
  
  .grid {
    grid-template-columns: 1fr;
  }
}
```

## Passo 6: Criando seu primeiro artigo

### 6.1. Formato do post

Crie um arquivo em `_posts/2025-01-01-meu-primeiro-post.md`:

```markdown
---
layout: post

title: "Meu primeiro post no blog"

date: 2025-01-01

excerpt: "Como criei meu blog no GitHub Pages e minhas primeiras impressões."

tags: [blog, github-pages, tecnologia]
---

# Meu primeiro post no blog

Este é meu primeiro artigo no blog! Aqui vou compartilhar...

## Subtítulo

Conteúdo do artigo com código:

```javascript
console.log("Hello, world!");
```

## Conclusão

Espero que tenham gostado!
```

### 6.2. Convenções importantes

- **Nome do arquivo**: `YYYY-MM-DD-titulo-do-post.md`
- **Front-matter obrigatório**: layout, title, date
- **Tags**: ajudam na organização
- **Excerpt**: resumo que aparece na listagem

## Passo 7: Deploy e configuração

### 7.1. Ativando GitHub Pages

1. Acesse **Settings** do seu repositório
2. Vá em **Pages** (menu lateral)
3. Em **Source**, selecione **Deploy from a branch**
4. Escolha **main** branch
5. Clique em **Save**

### 7.2. Primeiro deploy

```bash
# Adicione todos os arquivos
git add .

# Faça o commit
git commit -m "Initial blog setup with Jekyll"

# Envie para o GitHub
git push origin main
```

Aguarde alguns minutos e acesse `https://seuusername.github.io`

## Passo 8: Desenvolvimento local (opcional)

### 8.1. Usando GitHub Codespaces

1. No seu repositório, clique em **Code** → **Codespaces**
2. **Create codespace on main**
3. No terminal do Codespaces:

```bash
bundle install
bundle exec jekyll serve --host 0.0.0.0
```

### 8.2. Configuração local (Ruby)

```bash
# Instale Ruby (https://rubyinstaller.org/)
# Depois:
gem install jekyll bundler
bundle install
bundle exec jekyll serve
```

Acesse `http://localhost:4000` para ver o site local.

## Próximos passos

### Funcionalidades avançadas:

1. **Comentários**: Integração com Disqus
2. **Analytics**: Google Analytics
3. **SEO**: Meta tags e sitemap
4. **Domínio customizado**: `seublog.com`
5. **Tema personalizado**: Mais customizações

### Dicas importantes:

- **Backup**: Git já é seu backup automático
- **Versionamento**: Cada mudança fica registrada
- **Colaboração**: Outros podem contribuir via PR
- **Gratuito**: Zero custos de hospedagem

## Recursos úteis

- [Documentação Jekyll](https://jekyllrb.com/docs/)
- [GitHub Pages Docs](https://docs.github.com/pt/pages)
- [Liquid Template Language](https://shopify.github.io/liquid/)
- [Markdown Guide](https://www.markdownguide.org/)

---
