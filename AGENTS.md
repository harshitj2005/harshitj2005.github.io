# AGENTS.md — Project Instructions and Handoff

This file is the public, committable source of truth for AI collaborators working on
harshitjain.io. Keep it accurate after meaningful repository work.

## Required read order

1. Read this file fully.
2. If `.claude/OPERATING_INSTRUCTIONS.md` exists locally, read it.
3. If `.claude/PROJECT_CONTEXT.md` exists locally, read it.
4. Read the latest entries in `.claude/PROJECT_TIMELINE.md` when that file exists.
5. For post writing or revision, read `blog-post-instructions.md`.

Files under `.claude/`, `claude/`, and `seo-notes/` are intentionally local and ignored.
Do not copy, summarize, or expose their contents in tracked files, commits, public issues,
or published pages.

## Context and Git boundaries

- Keep project-specific context inside this repository.
- Do not read from, write to, or update the user's global/base Codex memory.
- After meaningful work, append a dated entry to `.claude/PROJECT_TIMELINE.md` if it exists.
- Never stage, commit, push, create a branch, or open a pull request unless explicitly asked.
- Preserve unrelated user changes in a dirty worktree.

## Project identity

- Site: `https://harshitjain.io`
- Owner: Harshit Jain
- Current title: Associate Principal Engineer at Nagarro
- Repository: `github.com/harshitj2005/harshitj2005.github.io`
- Host: GitHub Pages with a custom domain
- Theme: `jekyll-theme-chirpy ~> 7.0` as a gem
- Jekyll: `~> 4.3`
- Build: custom GitHub Actions workflow

Always use `Associate Principal Engineer`. `Senior Software Architect` is an obsolete title
and must not reappear.

## Public purpose and editorial positioning

The site is Harshit Jain's professional engineering presence and technical publication.
Content should build credible authority through original analysis, production architecture
decisions, research, and practical engineering insight.

Primary sections:

- Computing — distributed systems, GraphQL, microservices, Node.js/NestJS, cloud architecture
- Quantum — quantum computing, circuit simulation, communication systems
- AI — applied AI and engineering workflow analysis

Use an expert, first-person, production-grounded voice. Frame the site as technical writing,
original analysis, and published engineering work. Avoid hobby-blog or casual-diary framing.

## Technology stack

```text
Jekyll ~> 4.3
jekyll-theme-chirpy ~> 7.0
jekyll-seo-tag
jekyll-sitemap
jekyll-feed
jekyll-paginate
jekyll-archives
```

Important configuration:

- `url: "https://harshitjain.io"`
- `baseurl: ""`
- `permalink: /posts/:title/`
- Google Analytics: `G-4BPQ0QLNK1` through Chirpy's native analytics configuration
- `jekyll-archives.enabled: [tags]`
- Category archives remain disabled

## Repository map

```text
_config.yml                 Site configuration
_layouts/home.html          Custom homepage and Person JSON-LD
_includes/footer.html       Global footer override and image CSS
_includes/customize-head.html
                            Dead hook in the deployed Chirpy version; do not use
_includes/resume-section.html
                            Resume rendering partial
_tabs/                      About, Resume, Computing, Quantum, and AI pages
_posts/                     Published articles
_data/authors.yml           Post author mapping
_data/resume.yml            Resume content
assets/img/                 Public images
assets/files/               Public downloadable files
draw.io/                    Diagram sources
blog-post-instructions.md   Post creation workflow
.github/workflows/pages.yml Build and deploy workflow
```

## Post inventory

All posts use `author: harshit` and exactly one category from Computing, Quantum, or AI.

| File | Category | Status |
|---|---|---|
| `2025-05-05-when-your-upstream-goes-down-queue-based-microservice.md` | Computing | Live |
| `2026-03-13-quantum-diversity-combining.md` | Quantum | Live |
| `2026-04-10-qber-gate-noise-characterization.md` | Quantum | Live |
| `2026-05-14-defend-what-you-built-architecture-decision.md` | Computing | Live |
| `2026-06-27-agentic-coding-workflow-judgment.md` | AI | Live |
| `2026-06-27-message-queue-file-size-ceiling.md` | Computing | Live |

## Canonical post front matter

```yaml
---
layout: post
title: "[60 characters or fewer]"
date: YYYY-MM-DD
last_modified_at: YYYY-MM-DD
author: harshit
categories: [Computing]
tags: [tag-1, tag-2, tag-3, tag-4, tag-5]
description: "150–160 characters."
keywords: "keyword 1, keyword 2, keyword 3, keyword 4, keyword 5"
canonical_url: "https://harshitjain.io/posts/exact-filename-slug/"
image:
  path: /assets/img/post-slug-title.png
  alt: "Descriptive image alt text"
reading_time: "N min read"
toc: true
---
```

Rules:

- Category must be exactly one of `Computing`, `Quantum`, or `AI`.
- Canonical URL must match the filename slug and include a trailing slash.
- `image` must use object form with `path` and `alt`.
- `author: harshit` is required and must remain lowercase.
- `last_modified_at` must be updated when the article changes materially.
- Body images use absolute `/assets/...` paths and explicit dimensions.
- The visible author bio must use `Associate Principal Engineer`.
- The final article line must be:
  `<small>*Ideation and creation by human, written and formatted by AI*</small>`

## Content and confidentiality standards

- Lead with a non-obvious decision, tradeoff, experiment, or outcome.
- Make Harshit's contribution clear without exaggerated self-promotion.
- Prefer reusable field-level insight over generic tutorials.
- Check prose, captions, diagrams, alt text, and filenames for client, internal-system,
  confidential, or proprietary identifiers.
- Genericize sensitive context while preserving the technical lesson.
- Do not publish quantified business or production claims unless the user confirms they are
  approved for public use.
- Preserve established URLs when editing titles; title changes do not require slug changes.

## Structured data and identity

- BlogPosting is generated by `jekyll-seo-tag` on posts.
- Do not add a second BlogPosting emitter.
- Post author URL resolves through `_data/authors.yml` to
  `https://harshitjain.io/about/`.
- Person JSON-LD is present on the homepage and About page.
- LinkedIn references use
  `https://www.linkedin.com/in/harshitj2005/`.
- Google Analytics must remain configured only through `_config.yml`.

## Known theme and rendering issues

1. `_includes/customize-head.html` does not render in the deployed Chirpy version.
2. `_includes/footer.html` is pulled through a cached include. Page-dependent Liquid placed
   there freezes and can leak one page's values across the site.
3. The current BreadcrumbList block in `footer.html` is therefore incorrect on live pages.
   Remove it before adding a replacement through a verified non-cached per-page hook.
4. `/resume/`, `/computing/`, `/quantum/`, and `/ai/` currently render
   `<title> | Harshit Jain</title>`.
5. Those non-post pages also receive inappropriate BlogPosting structured data.
6. Category archives must remain disabled; custom tab pages serve as category landing pages.
7. The `github-pages` gem must not be added because it pins an incompatible Jekyll version.
8. GitHub Pages source must remain set to GitHub Actions, not Deploy from branch.

Validate rendered and live output rather than trusting source configuration alone.

## Deployment

Pushes to `main` trigger:

```text
Checkout
→ Ruby 3.3
→ bundle install
→ JEKYLL_ENV=production jekyll build
→ actions/deploy-pages@v4
→ harshitjain.io
```

Do not push automatically. When the user handles deployment, allow approximately 60–90
seconds, then verify the workflow and live pages.

## Current priorities

1. Fix blank titles and incorrect structured data on non-post pages.
2. Remove the frozen BreadcrumbList and reintroduce it through a verified per-page hook.
3. Align `README.md` and `blog-post-instructions.md` with the six-post inventory.
4. Improve internal links from the homepage, About page, and related articles.
5. Review sensitive filenames, public claims, and contact information.
6. Bring three long titles and three off-target descriptions into current editorial ranges
   without changing established slugs.
7. Continue a sustainable publishing cadence across Computing, Quantum, and AI.

## Documentation update rules

After meaningful work:

1. Update this file only when public technical facts, rules, inventory, or priorities change.
2. Keep `CLAUDE.md` as a compatibility entrypoint; do not duplicate this entire file there.
3. Update `blog-post-instructions.md` when writing rules or the post index changes.
4. Append the dated work and decision record to `.claude/PROJECT_TIMELINE.md`.
5. Update `.claude/PROJECT_CONTEXT.md` only when private current state or strategy changes.
6. Before handoff, scan tracked files to ensure private local context has not leaked.

