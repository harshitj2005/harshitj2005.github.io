---
layout: page
title: Computing
icon: fas fa-microchip
order: 3
description: >-
  Technical writing by Harshit Jain on distributed systems, microservices
  architecture, GraphQL, API design, cloud infrastructure, and software
  engineering craft.
---

Deep dives into distributed systems, microservices architecture, API design, cloud infrastructure, and software engineering craft.

---

{% assign cat_posts = site.posts | where_exp: "post", "post.categories contains 'Computing'" %}
{% if cat_posts.size > 0 %}
  {% for post in cat_posts %}
<article class="card-wrapper card mb-3">
  <a href="{{ post.url | relative_url }}" class="post-preview d-block text-decoration-none p-3">
    <h3 class="post-title mb-1">{{ post.title }}</h3>
    <div class="post-meta text-muted small mb-2">
      <i class="far fa-calendar-alt fa-fw me-1"></i>
      <time>{{ post.date | date: "%B %d, %Y" }}</time>
    </div>
    {% if post.excerpt %}
    <p class="post-excerpt text-muted mb-0">{{ post.excerpt | strip_html | truncate: 220 }}</p>
    {% endif %}
  </a>
</article>
  {% endfor %}
{% else %}
*First post coming soon. Stay tuned.*
{% endif %}
