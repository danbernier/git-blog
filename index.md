---
title: 'generative art'
layout: front
---

## Projects

{% for post in site.posts %}
### [{{ post.title }}]({{site.baseurl}}{{ post.url }})

{{ post.tagline }}

{{ post.timeline }}

{% if post.thumbnail %}![thumbnail]({{site.baseurl}}/images/{{ post.thumbnail }}){% endif %}
{% endfor %}
