---
title: 'Adventures in RF'
content:
    items: '@self.children'
    order:
        by: date
        dir: desc
    limit: 10
    pagination: true
process:
    markdown: true
    twig: true
---

Here I'll document some of my adventures in RF. Please forgive the very amateur nature, incorrect terminology etc...

<ul>
  {% for p in page.collection %}
    <li><a href="{{ p.url }}">{{ p.title }}</a></li>
  {% endfor %}
</ul>