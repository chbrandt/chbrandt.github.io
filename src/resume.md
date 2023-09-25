---
title: Resume
layout: "base.njk"
---

## Overview

Lorum ipsum.

## Education

<ul>
{% for item in resume.education %}
    <li>
        {{ item.title }} in {{ item.area }} <br> ( {{ item.topic }} )
        <ul>
            <li>{{ item.institution.name }}</li>
        </ul>
    </li>
{% endfor %}
</ul>
