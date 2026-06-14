---
layout: default
body_class: home-page
---

{% assign posts = site.posts %}

{% if posts.size > 0 %}
<div class="blog-list">
{% for post in posts %}
  {% assign summary = post.content | markdownify | strip_html | strip_newlines | replace: "  ", " " | truncate: 200 %}
  <article class="blog-card">
    <h2 class="blog-title">
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
    </h2>
    <p class="blog-meta">{{ post.date | date: "%Y-%m-%d" }}</p>
    <p class="blog-summary">{{ summary }}</p>
    <p class="blog-actions">
      <a class="blog-link" href="{{ post.url | relative_url }}">继续阅读</a>
    </p>
  </article>
{% endfor %}
</div>
{% else %}
暂无文章。
{% endif %}
