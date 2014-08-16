---
layout: page
title: Blog Posts
---

{% for post in site.posts %}
  * [ {{ post.title }} ]({{ post.url }}) <span style="font-size:0.6em"> [{{post.date | date_to_string }}]</span>
{% endfor %}