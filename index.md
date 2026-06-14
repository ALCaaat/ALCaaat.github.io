---
layout: page
title: 首页
---

{% assign posts = site.posts %}

{% if posts.size > 0 %}
<div class="blog-list">
{% for post in posts %}
  {% assign summary = post.content | markdownify | strip_html | strip_newlines | replace: "  ", " " | truncate: 200 %}
  {% assign cover = post.image | default: post.cover %}
  <article class="blog-card">
    <a class="blog-cover" href="{{ post.url | relative_url }}" aria-label="{{ post.title }}">
      {% if cover %}
        <img src="{{ cover | relative_url }}" alt="{{ post.title }}">
      {% else %}
        <span class="blog-cover-placeholder">{{ post.title | slice: 0, 1 }}</span>
      {% endif %}
    </a>
    <div class="blog-content">
      <p class="blog-meta">{{ post.date | date: "%Y-%m-%d" }}</p>
      <h2 class="blog-title"><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h2>
      <p class="blog-summary">{{ summary }}</p>
      <p><a class="blog-link" href="{{ post.url | relative_url }}">继续阅读</a></p>
    </div>
  </article>
{% endfor %}
</div>
{% else %}
暂无文章。
{% endif %}
