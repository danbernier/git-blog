---
title: Home again, home again
layout: front
---

{{ page }}

## Projects

{% for post in site.posts %}
  * [{{ post.title }}]({{ post.url }})
{% endfor %}
