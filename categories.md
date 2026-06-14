---
layout: default
title: 分类
permalink: /categories/
---

{% assign categories = site.categories | sort %}

<section class="page-section">
  <header class="section-header">
    <p class="section-kicker">Categories</p>
    <h1 class="section-title">分类</h1>
  </header>

{% if categories.size > 0 %}
<div class="category-list">
{% for category in categories %}
{% assign posts = category[1] %}
<section class="category-card">
  <p class="category-count">{{ posts.size }} 篇</p>
  <h2 class="category-title">
    <a class="category-link" href="{{ '/category/?name=' | relative_url }}{{ category[0] | uri_escape }}">{{ category[0] }}</a>
  </h2>
  <ul class="category-posts">
  {% for post in posts limit:3 %}
    <li>
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      <span>{{ post.date | date: "%Y-%m-%d" }}</span>
    </li>
  {% endfor %}
  </ul>
  <p><a class="blog-link" href="{{ '/category/?name=' | relative_url }}{{ category[0] | uri_escape }}">查看更多</a></p>
</section>
{% endfor %}
</div>
{% else %}
暂无分类。
{% endif %}
</section>
