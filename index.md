---
layout: default
title: "Quantemplative"
---

Hi, I'm [Dr Ralph Rudd](/about) and this is my academic blog.

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>