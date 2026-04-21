# Claude Code Prompt: Personal GitHub Pages Site (Jekyll)

> **How to use this file:** Open Claude Code in your terminal, paste this entire file as your first message, and it will scaffold the complete Jekyll site for you. Run this in a new empty directory that will become your GitHub repo.

---

## Project Overview

Build a **Jekyll-based GitHub Pages personal website** for Harshit Jain — a Senior Software Architect with 10+ years of experience. The site will have three pages:

1. **Home** — Professional bio and intro
2. **Resume** — Full resume displayed as a styled web page
3. **Blog** — Blog listing page (no posts yet, just the scaffolding)

The site must be deployable to GitHub Pages with zero configuration, support a custom domain, and use a clean, developer-appropriate theme. All content is placeholder/draft — final copy will be updated separately.

---

## Tech Stack & Constraints

- **Static site generator:** Jekyll (GitHub Pages native — no custom build action needed)
- **Theme:** [Chirpy](https://github.com/cotes2004/jekyll-theme-chirpy) — professional, dark/light mode, blog-ready, widely used by engineers
- **Hosting:** GitHub Pages (free, public repo)
- **Custom domain:** Will be configured later (leave placeholder in `_config.yml`)
- **No WordPress, no Node.js, no databases** — purely static
- **No npm or webpack** — keep it Jekyll-native so GitHub Pages builds it automatically on push

---

## Repository Structure to Create

```
/
├── _config.yml              # Jekyll + Chirpy configuration
├── Gemfile                  # Ruby gems (jekyll, chirpy theme)
├── .gitignore
├── index.md                 # Home page (layout: home)
├── resume.md                # Resume page (layout: page)
├── blog/
│   └── index.html           # Blog listing page (layout: blog)
├── _posts/                  # Empty for now — blog posts go here later
│   └── .gitkeep
├── _data/
│   └── resume.yml           # Structured resume data (pulled from below)
├── _includes/
│   └── resume-section.html  # Reusable resume section include
├── assets/
│   └── img/
│       └── avatar.jpg       # Placeholder — user will replace
└── _tabs/                   # Chirpy uses _tabs for nav items
    ├── about.md
    ├── resume.md
    └── blog.md
```

---

## Step-by-Step Instructions for Claude Code

### Step 1 — Initialize the repo with Chirpy theme

Use the [Chirpy Starter](https://github.com/cotes2004/chirpy-starter) method (not gem-based fork) because GitHub Pages builds it cleanly:

```bash
# Claude Code should run these commands
git init
echo "source 'https://rubygems.org'" > Gemfile
echo "gem 'github-pages', group: :jekyll_plugins" >> Gemfile
echo "gem 'jekyll-theme-chirpy'" >> Gemfile
```

### Step 2 — Create `_config.yml`

```yaml
# _config.yml
title: Harshit Jain
tagline: Senior Software Architect · GraphQL · Microservices · Node.js
description: >-
  Personal site and technical blog of Harshit Jain — Associate Principal Engineer
  at Nagarro, specializing in distributed systems, microservices architecture, and
  scalable GraphQL APIs.

url: "https://yourusername.github.io"   # UPDATE: replace with actual GitHub username
baseurl: ""                              # Leave empty for apex domain; set to /repo-name if using project page

github:
  username: yourusername                 # UPDATE

social:
  name: Harshit Jain
  email: Harshitj2005@gmail.com
  links:
    - https://linkedin.com/in/yourprofile  # UPDATE

theme: jekyll-theme-chirpy

# Timezone
timezone: America/New_York

# Pagination for blog
paginate: 10

# Collections
collections:
  tabs:
    output: true
    sort_by: order

defaults:
  - scope:
      path: ""
      type: posts
    values:
      layout: post
      comments: false
      toc: true
  - scope:
      path: ""
      type: tabs
    values:
      layout: page
      permalink: /:title/

# Navigation order
navigation:
  - title: Home
    url: /
  - title: Resume
    url: /resume/
  - title: Blog
    url: /blog/

exclude:
  - "*.gem"
  - "*.gemspec"
  - Gemfile.lock
  - vendor
  - README.md
```

### Step 3 — Create Home Page (`index.md`)

```markdown
---
layout: home
title: Home
---
```

> Note: Chirpy's `home` layout auto-pulls from `_config.yml` tagline and recent posts. 
> The actual bio content will go in `_tabs/about.md` — see Step 5.

### Step 4 — Create About/Bio Page (`_tabs/about.md`)

```markdown
---
layout: page
title: About
icon: fas fa-user
order: 1
---

## Hi, I'm Harshit Jain

I'm an Associate Principal Engineer at **Nagarro**, based in Pennsylvania, USA, with 10+ years of experience building scalable distributed systems and microservices architectures.

I specialize in **GraphQL**, **Node.js/TypeScript**, and **NestJS**, with a focus on resilient system design, API architecture, and engineering leadership. I've led teams of 20+ engineers and driven large-scale digital transformation programs across telecom, construction, and e-commerce domains.

Currently, I'm deepening my expertise in **quantum computing and AI integration** through a Post-Graduate Diploma at IIT Delhi.

---

### What I Work On

- Distributed microservices architecture (Saga pattern, circuit breakers, event-driven design)
- GraphQL federation and schema design
- API performance optimization (Redis caching, query tuning)
- Cloud infrastructure (AWS, Azure, GCP)
- Mentoring engineers and driving technical strategy

---

### Currently Exploring

- Quantum-classical system integration (IIT Delhi CEPQIP program)
- IEEE/ACM research publication opportunities
- Writing about architecture patterns and system design

---

### Get In Touch

- **Email:** Harshitj2005@gmail.com
- **LinkedIn:** [linkedin.com/in/yourprofile](#)  <!-- UPDATE -->
- **Phone:** +1-484-536-9012
```

### Step 5 — Create Resume Page (`_tabs/resume.md`)

This page renders structured data from `_data/resume.yml` using a custom include. It is a **web page** — not a PDF download — styled to match the site theme. A PDF download link can be added later if desired.

```markdown
---
layout: page
title: Resume
icon: fas fa-file-alt
order: 2
---

{% include resume-section.html %}

---

*Available for senior architecture roles, consulting, and speaking engagements.*

[📄 Download PDF version](#)  <!-- UPDATE: add link to PDF once hosted in /assets/ -->
```

### Step 6 — Create `_data/resume.yml` (structured resume data)

```yaml
# _data/resume.yml
# Sourced from Harshit Jain's resume — update as needed

contact:
  phone: "+1-484-536-9012"
  email: "Harshitj2005@gmail.com"
  linkedin: "linkedin.com/in/yourprofile"

summary: >
  Technologist with 10+ years in scalable architecture and microservices,
  specializing in JavaScript/TypeScript, Node.js, and GraphQL. Proven track
  record in delivering tech-forward solutions integrating third-party SaaS
  tools and automation to enhance operational efficiency.

skills:
  languages: [JavaScript, TypeScript, PHP]
  frameworks: [NestJS, Node.js, GraphQL, Symfony3]
  databases: [MySQL, MongoDB, Redis]
  cloud: [AWS, Azure, GCP]
  tools: [Docker, Kubernetes, Kafka, RabbitMQ, Camunda BPMN, OpenShift]
  patterns: [Microservices, Saga, Circuit Breaker, GraphQL Federation, REST]

certifications:
  - Google Cloud Professional Cloud Architect
  - Google Cloud Professional Cloud Developer
  - Professional Scrum Master (PSM 1)
  - ICAgile Certified Professional – Foundations of AI

education:
  - degree: Bachelor of Technology (B.Tech) — Computer Science & Engineering
    institution: Kurukshetra University, Haryana, India
    year: "2010 – 2014"
    notes:
      - "CGPA: 7.2/10.0"
      - "20th Rank in CSE department"
      - Merit holder

experience:
  - company: Nagarro Software
    roles:
      - title: Associate Principal Engineer
        period: "Nov 2023 – Present"
        location: Pennsylvania, USA
        highlights:
          - Architected GraphQL schema design that reduced data over-fetching by 40%
          - Orchestrated business logic using GraphQL to abstract downstream communication with Autodesk, MuleSoft, and Mendex
          - Integrated with Revit to automate construction site design and delivery workflows, reducing project timelines by 30%
          - Implemented GraphQL federation enabling autonomous team development while maintaining unified API schema, increasing velocity by 25%

      - title: Senior Staff Engineer
        period: "May 2022 – Nov 2023"
        location: Pennsylvania, USA
        highlights:
          - Led microservices platform architecture using Node.js and NestJS, improving scalability and resiliency
          - Rewrote order fulfillment system with Saga pattern for auto-refunds, reducing customer service tickets by 70% and increasing revenue by 20%
          - Integrated New Relic telemetry dashboards and alerts, reducing MTTR by 60%
          - Optimized database queries and caching strategies, reducing API response times by 85%

      - title: Staff Engineer
        period: "Apr 2021 – Apr 2022"
        location: Noida, India
        highlights:
          - Led development team of 20+ engineers across microservices architecture
          - Redesigned critical APIs reducing response time from 200ms to 4ms using Redis, Fastify, and NestJS
          - Implemented circuit breaker patterns improving system resilience by 90%

      - title: Associate Staff Engineer
        period: "Apr 2019 – Mar 2021"
        location: Gurugram, India
        highlights:
          - Telco Lead for digital transformation of a major Middle Eastern telecom operator
          - Orchestrated BSS, Ericsson Mobile Activation, and government system (SIMATI, ABSHER) integration via Camunda BPMN
          - Built containerized microservices on OpenShift for fully digital onboarding and self-care
          - Developed RabbitMQ services processing 1M+ async operations/day at 99.9% reliability

      - title: Senior Software Engineer
        period: "Oct 2017 – Mar 2019"
        location: Gurugram, India
        highlights:
          - Built RESTful APIs on Symfony3 with 40ms average response time
          - Contributed to technical architecture decisions and full SDLC delivery

  - company: GoldVIP Technology Solutions (Crown It)
    roles:
      - title: Senior Software Engineer
        period: "Jun 2015 – Oct 2017"
        location: Gurugram, India
        highlights:
          - Rebuilt mobile app backend in Node.js, improving performance by 300%
          - Developed async data-processing middleware, reducing processing time by 70%
          - Created in-house Communication Manager for targeted marketing, increasing campaign effectiveness by 45%
          - Led AWS to Azure migration, improving cloud cost efficiency by 25%

  - company: FierceHound Media & Consulting
    roles:
      - title: Senior Associate Web Development
        period: "Jun 2014 – Jun 2015"
        location: Gurugram, India
        highlights:
          - Developed web applications using PHP MVC frameworks (CakePHP, YII 2.0)

  - company: Web Expert Online
    roles:
      - title: Web Developer
        period: "Dec 2013 – Jun 2014"
        location: New Delhi, India
        highlights:
          - Developed web software using PHP, WordPress, and Joomla
          - Created custom WordPress plugins optimizing site performance by 35%
```

### Step 7 — Create `_includes/resume-section.html`

This include loops through `_data/resume.yml` and renders it as a styled HTML page.

```html
<!-- _includes/resume-section.html -->

<div class="resume">

  <!-- Summary -->
  <section class="resume-summary">
    <p>{{ site.data.resume.summary }}</p>
  </section>

  <!-- Skills -->
  <section>
    <h2>Skills</h2>
    <table>
      <tr><td><strong>Languages</strong></td><td>{{ site.data.resume.skills.languages | join: ", " }}</td></tr>
      <tr><td><strong>Frameworks</strong></td><td>{{ site.data.resume.skills.frameworks | join: ", " }}</td></tr>
      <tr><td><strong>Databases</strong></td><td>{{ site.data.resume.skills.databases | join: ", " }}</td></tr>
      <tr><td><strong>Cloud</strong></td><td>{{ site.data.resume.skills.cloud | join: ", " }}</td></tr>
      <tr><td><strong>Tools</strong></td><td>{{ site.data.resume.skills.tools | join: ", " }}</td></tr>
      <tr><td><strong>Patterns</strong></td><td>{{ site.data.resume.skills.patterns | join: ", " }}</td></tr>
    </table>
  </section>

  <!-- Experience -->
  <section>
    <h2>Experience</h2>
    {% for job in site.data.resume.experience %}
      <h3>{{ job.company }}</h3>
      {% for role in job.roles %}
        <div class="role">
          <div class="role-header">
            <strong>{{ role.title }}</strong>
            <span class="period">{{ role.period }} · {{ role.location }}</span>
          </div>
          <ul>
            {% for item in role.highlights %}
              <li>{{ item }}</li>
            {% endfor %}
          </ul>
        </div>
      {% endfor %}
    {% endfor %}
  </section>

  <!-- Education -->
  <section>
    <h2>Education</h2>
    {% for edu in site.data.resume.education %}
      <div class="role">
        <strong>{{ edu.degree }}</strong><br>
        {{ edu.institution }} · {{ edu.year }}<br>
        <ul>
          {% for note in edu.notes %}
            <li>{{ note }}</li>
          {% endfor %}
        </ul>
      </div>
    {% endfor %}
  </section>

  <!-- Certifications -->
  <section>
    <h2>Certifications</h2>
    <ul>
      {% for cert in site.data.resume.certifications %}
        <li>{{ cert }}</li>
      {% endfor %}
    </ul>
  </section>

</div>

<style>
  .resume section { margin-bottom: 2rem; }
  .resume h2 { border-bottom: 1px solid var(--border-color); padding-bottom: 0.3rem; }
  .role { margin-bottom: 1.2rem; }
  .role-header { display: flex; justify-content: space-between; flex-wrap: wrap; }
  .period { color: var(--text-muted-color); font-size: 0.9rem; }
  .resume table { width: 100%; border-collapse: collapse; }
  .resume table td { padding: 0.3rem 0.5rem; vertical-align: top; }
  .resume table td:first-child { width: 140px; white-space: nowrap; }
</style>
```

### Step 8 — Create Blog Page (`_tabs/blog.md`)

```markdown
---
layout: page
title: Blog
icon: fas fa-pen-nib
order: 3
---

## Writing

I write about distributed systems, architecture patterns, GraphQL, and engineering leadership.
Posts are infrequent but in-depth — quality over volume.

---

{% if site.posts.size > 0 %}
{% for post in site.posts %}
### [{{ post.title }}]({{ post.url }})
*{{ post.date | date: "%B %d, %Y" }}*

{{ post.excerpt }}

---
{% endfor %}
{% else %}
*First post coming soon. Stay tuned.*
{% endif %}
```

### Step 9 — Create `.gitignore`

```
_site/
.jekyll-cache/
.jekyll-metadata
vendor/
Gemfile.lock
.DS_Store
```

### Step 10 — Create `_posts/.gitkeep`

Just an empty file to preserve the directory in Git.

### Step 11 — README for the repo

```markdown
# harshitjain.dev (or yourusername.github.io)

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

Push to `main` branch → GitHub Actions builds and deploys automatically.

## Custom domain setup (GoDaddy)

1. Add these A records in GoDaddy DNS:
   - `185.199.108.153`
   - `185.199.109.153`
   - `185.199.110.153`
   - `185.199.111.153`
2. Add CNAME: `www` → `yourusername.github.io`
3. In repo Settings → Pages → Custom Domain → enter your domain
4. Check "Enforce HTTPS" after certificate provisions (~10 min)
```

---

## GitHub Repo Setup Instructions (Do After Claude Code Runs)

After the scaffolding is complete, run these commands:

```bash
# Initialize git and push
git add .
git commit -m "Initial Jekyll site setup"

# Create repo on GitHub (replace with your username and desired repo name)
# Repo name should be: yourusername.github.io for apex GitHub Pages
git remote add origin https://github.com/yourusername/yourusername.github.io.git
git branch -M main
git push -u origin main
```

Then in GitHub:
- Go to repo **Settings → Pages**
- Source: **Deploy from a branch** → `main` → `/ (root)`
- Site will be live at `https://yourusername.github.io` within 2-3 minutes

---

## Resume: Web Page vs PDF — Design Decision

The resume is a **web page** (not a PDF embed), for these reasons:

- It's searchable and indexable by Google — good for EB1A visibility
- It renders correctly on mobile without PDF viewer issues
- It's easy to update — edit `_data/resume.yml` and push
- It matches the site's theme and dark/light mode

**If you also want a PDF download link:** Upload your `Harshit_Jain_2025.pdf` to `/assets/files/Harshit_Jain_Resume.pdf` in the repo. The resume page already has a placeholder `[Download PDF](#)` link — update the `#` to `/assets/files/Harshit_Jain_Resume.pdf`.

---

## What Stays Out of This Repo (Handled Separately)

- **Email:** Zoho Mail with IMAP in Apple Mail — DNS MX records set in GoDaddy
- **Domain purchase:** GoDaddy — configure DNS A records per README above
- **Final bio copy and blog post content** — separate conversation

---

## Notes for Claude Code

- Do not install any npm packages — Jekyll only
- Do not create a GitHub Actions workflow — GitHub Pages handles Jekyll builds natively
- If Chirpy theme gem has compatibility issues with `github-pages` gem, fall back to `minima` theme and note it
- Keep all content files as `.md` not `.html` where possible
- Validate that `_config.yml` is valid YAML before finishing
- Run `bundle exec jekyll build` at the end to verify the site builds without errors
