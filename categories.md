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

共 {{ posts.size }} 篇

<ul>
{% for post in posts limit:3 %}
  <li>
    <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
    <span>{{ post.date | date: "%Y-%m-%d" }}</span>
  </li>
{% endfor %}
</ul>

<p><a href="{{ '/category/?name=' | relative_url }}{{ category[0] | uri_escape }}">更多</a></p>

{% endfor %}
{% else %}
暂无分类。
{% endif %}
