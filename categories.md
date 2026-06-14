---
layout: page
title: 分类
permalink: /categories/
---

{% assign categories = site.categories | sort %}

{% if categories.size > 0 %}
  {% for category in categories %}
## {{ category[0] }}

    {% assign posts = category[1] %}
    <ul>
    {% for post in posts %}
      <li>
        <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
        <span>{{ post.date | date: "%Y-%m-%d" }}</span>
      </li>
    {% endfor %}
    </ul>
  {% endfor %}
{% else %}
暂无分类。
{% endif %}
