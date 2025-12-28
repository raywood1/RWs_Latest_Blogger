---
layout: default
title: Archive
---

{% for post in site.posts %}
* [{{ post.title }}]({{ post.url }}) — {{ post.date | date: "%Y" }}
{% endfor %}
