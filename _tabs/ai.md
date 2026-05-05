---
layout: page
title: AI
icon: fas fa-brain
order: 5
---

## AI

Thoughts on AI integration in software systems, practical applications, and the evolving role of AI in engineering and architecture.

To tag a post for this section, add `AI` to its `categories` front matter:

```yaml
categories: [AI]
```

---

{% assign cat_posts = site.posts | where_exp: "post", "post.categories contains 'AI'" %}
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
