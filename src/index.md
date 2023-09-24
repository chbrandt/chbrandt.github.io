---
title: Hallo Welt
layout: "base.njk"
---

Hallo, Carlos!

{% for post in collections.posts %}

- [{{ post.data.title }}]({{ post.url }})

{% endfor %}
