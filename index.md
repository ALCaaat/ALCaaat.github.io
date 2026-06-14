---
layout: page
title: 首页
---

{% assign posts = site.posts %}

{% if posts.size > 0 %}
<ul>
{% for post in posts %}
  <li>
    <h2><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h2>
    <p>{{ post.date | date: "%Y-%m-%d" }}</p>
    <p>{{ post.excerpt | strip_html | strip_newlines | truncate: 140 }}</p>
  </li>
{% endfor %}
</ul>
{% else %}
暂无文章。
{% endif %}
