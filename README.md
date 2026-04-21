# harshitj2005.github.io

Personal website and blog built with Jekyll + Chirpy theme, hosted on GitHub Pages.

## Local development

```bash
bundle install
bundle exec jekyll serve
```

Open http://localhost:4000

## Adding a blog post

Create a file in `_posts/` named `YYYY-MM-DD-title-of-post.md`:

```markdown
---
title: "Your Post Title"
date: 2026-04-21
categories: [Architecture, GraphQL]
tags: [graphql, microservices, nodejs]
---

Your post content in Markdown here.
```

Push to `main` branch — GitHub Pages builds and deploys automatically.

## Custom domain setup (GoDaddy)

1. Add these A records in GoDaddy DNS:
   - `185.199.108.153`
   - `185.199.109.153`
   - `185.199.110.153`
   - `185.199.111.153`
2. Add CNAME: `www` → `harshitj2005.github.io`
3. In repo Settings → Pages → Custom Domain → enter your domain
4. Check "Enforce HTTPS" after certificate provisions (~10 min)
