---
layout: page
title: Quantum
icon: fas fa-atom
order: 4
---

## Quantum

Explorations in quantum computing, quantum-classical hybrid systems, and my journey through the CEPQIP program at IIT Delhi.

To tag a post for this section, add `Quantum` to its `categories` front matter:

```yaml
categories: [Quantum]
```

---

{% assign cat_posts = site.posts | where_exp: "post", "post.categories contains 'Quantum'" %}
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
