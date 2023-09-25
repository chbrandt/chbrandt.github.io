---
title: Hallo Welt
layout: "base.njk"
---

Hallo, Carlos!

{% for post in collections.post %}

- [{{ post.data.title }}]({{ post.url }})

{% endfor %}
