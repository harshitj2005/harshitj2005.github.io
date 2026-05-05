---
layout: page
title: Computing
icon: fas fa-microchip
order: 3
---

## Computing

Deep dives into distributed systems, microservices architecture, API design, cloud infrastructure, and software engineering craft.

To tag a post for this section, add `Computing` to its `categories` front matter:

```yaml
categories: [Computing]
```

---

{% assign cat_posts = site.posts | where_exp: "post", "post.categories contains 'Computing'" %}
{% if cat_posts.size > 0 %}
  {% for post in cat_posts %}
### [{{ post.title }}]({{ post.url }})
*{{ post.date | date: "%B %d, %Y" }}*

{{ post.excerpt }}

---
  {% endfor %}
{% else %}
*First post coming soon. Stay tuned.*
{% endif %}
