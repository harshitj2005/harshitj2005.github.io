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
