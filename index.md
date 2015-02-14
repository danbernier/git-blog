---
title: 'generative art'
layout: front
---

## Projects

{% for post in site.posts %}
### [{{ post.title }}]({{site.baseurl}}{{ post.url }})

{{ post.tagline }}

<div class="timeline">{{ post.timeline }}</div>

{% if post.thumbnail %}![thumbnail]({{site.baseurl}}/images/{{ post.thumbnail }}){% endif %}
{% endfor %}
