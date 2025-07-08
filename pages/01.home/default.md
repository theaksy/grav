---
title: Home
body_classes: 'title-center title-h1h2'
content:
    items: '@root.pages'
process:
    twig: true
    markdown: false
twig_first: true
---

<ul>
  {% for p in page.collection %}
    <li><a href="{{ p.url }}">{{ p.title }}</a></li>
  {% endfor %}
</ul>