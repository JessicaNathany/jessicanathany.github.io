---
layout: post

title: "How to Create a Complete Blog on GitHub Pages with Jekyll - Definitive Guide"

date: 2025-12-30

lang: en

cover: "/assets/img/githubpages.png"

excerpt: "Complete step-by-step guide to create your own blog on GitHub Pages using Jekyll, from initial setup to publishing articles."

tags: [github-pages, jekyll, blog, tutorial]
---

## How to Create a Complete Blog on GitHub Pages with Jekyll - Definitive Guide

Creating a technical blog is an excellent way to share knowledge and build your online presence as a developer. In this complete guide, I'll show you how to create a professional blog on GitHub Pages using Jekyll, completely free and with a custom domain.

## Why GitHub Pages?

- **Free** - No hosting costs
- **Git Integration** - Automatic versioning  
- **Integrated Jekyll** - Static site generator
- **Custom Domain** - `yourusername.github.io`
- **Automatic HTTPS** - Security included
- **Automatic Deploy** - On every push

## Step 1: Initial Setup

### 1.1. Creating the repository

1. **Access GitHub** and create a new repository
2. **Required name**: `yourusername.github.io` (replace with your username)
3. **Mark as public** (required for free accounts)
4. **Add an initial README.md**

```bash
# Clone the repository
git clone https://github.com/yourusername/yourusername.github.io.git

cd yourusername.github.io
```

### 1.2. Folder structure

Create the following structure:

```
yourusername.github.io/
├── _config.yml          # Jekyll configurations
├── _layouts/            # Site templates
│   ├── default.html
│   └── post.html
├── _posts/              # Your articles
├── assets/              # CSS, images, JS
│   ├── css/
│   └── img/
├── index.md             # Home page
├── articles.md          # Articles list
├── about.md            # About you
└── Gemfile              # Ruby dependencies
```

## Step 2: Setting up Jekyll

### 2.1. `_config.yml` file

```yaml
title: "Your Name"

description: "Your blog about development and technology"

author: "Your Name"

url: "https://yourusername.github.io"

baseurl: ""

markdown: kramdown

# Build settings
plugins:
  - jekyll-feed

# Navigation
nav:
  - label: "About"
    url: "/about"
  - label: "Articles"
    url: "/articles"
  - label: "Projects"
    url: "/projects"

# Permalinks
permalink: /articles/:title/
```
