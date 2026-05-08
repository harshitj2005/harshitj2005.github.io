# harshitjain.io

Personal website and technical blog of **Harshit Jain** — Associate Principal Engineer specializing in distributed systems, GraphQL federation, and microservices architecture.

Live at → **[harshitjain.io](https://harshitjain.io)**

---

## What's here

This is the source for my personal site: long-form technical writing, architecture deep dives, and occasional explorations into quantum computing. Topics I write about:

- **Distributed systems** — Saga patterns, compensating transactions, fault isolation, event-driven design
- **GraphQL** — Federation, schema design at scale, performance trade-offs
- **Node.js / NestJS / TypeScript** — Service architecture, performance engineering, production patterns
- **Cloud infrastructure** — GCP, Azure, Kubernetes, deployment topology
- **Quantum computing** — My ongoing journey through the IIT Delhi CEPQIP program

I write because explaining things clearly is the best way to find out if you actually understand them. If something I've written saves you a debugging session or shortcuts a design decision, that's the whole point.

---

## Stack

Built with **[Jekyll](https://jekyllrb.com/)** + **[Chirpy theme](https://github.com/cotes2333/jekyll-theme-chirpy)**, hosted on **GitHub Pages**. No build servers, no CI pipelines, no dependencies to babysit — just Markdown files and a `git push`.

---

## Running locally

```bash
# Prerequisites: Ruby >= 3.1, Bundler
gem install bundler

# Install dependencies
bundle install

# Serve with live reload
bundle exec jekyll serve --livereload
```

Open [http://localhost:4000](http://localhost:4000)

---

## Writing a post

Create a file under `_posts/` following the naming convention:

```
_posts/YYYY-MM-DD-your-post-slug.md
```

Frontmatter template:

```yaml
---
title: "Your Post Title"
date: 2026-05-07
categories: [Computing]        # Computing | AI | Quantum
tags: [graphql, microservices, nestjs]
description: "One or two sentences for SEO and social previews."
---

Post content in Markdown.
```

**Available categories:** `Computing`, `AI`, `Quantum`

Push to `main` — GitHub Pages builds and deploys automatically. Usually live within ~60 seconds.

---

## Custom domain (optional)

If you're forking this and want to use your own domain via GoDaddy (or any registrar):

1. Add these `A` records pointing to GitHub Pages:
   ```
   185.199.108.153
   185.199.109.153
   185.199.110.153
   185.199.111.153
   ```
2. Add a `CNAME` record: `www` → `<your-username>.github.io`
3. In repo **Settings → Pages → Custom Domain**, enter your domain
4. Enable **Enforce HTTPS** after the certificate provisions (~10 min)

---

## Project structure

```
.
├── _data/
│   └── resume.yml          # Resume data (powers the /resume page)
├── _includes/
│   └── resume-section.html # Resume layout template
├── _layouts/
│   └── home.html           # Custom home page layout
├── _posts/                 # Blog posts (YYYY-MM-DD-slug.md)
├── assets/
│   ├── img/avatar.jpg      # Profile photo
│   └── files/              # Downloadable files (resume PDF, etc.)
├── computing.md            # Computing category page
├── ai.md                   # AI category page
├── quantum.md              # Quantum category page
├── resume.md               # Resume page
├── index.md                # Home page content
└── _config.yml             # Site configuration
```

---

## Resume data

The `/resume` page is driven by `_data/resume.yml`. Edit that file to update job history, skills, certifications, and education — the HTML template renders it automatically. No HTML editing required.

---

## Contributing / Feedback

If you spot a technical error in a post, have a question about something I wrote, or want to discuss an architecture trade-off — open an issue. I read them.

If you're forking this as a starting point for your own site: go for it. The structure is intentionally simple so you can strip out what you don't need and make it yours.

---

## License

Blog posts and written content: **[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)** — you can share and adapt with attribution.  
Code and templates in this repo: **MIT**