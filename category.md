---
layout: page
title: 分类详情
permalink: /category/
---

<section class="category-card">
  <div class="category-heading">
    <div class="category-heading-main">
      <h1 id="category-title" class="category-title">分类详情</h1>
      <span id="category-badge" class="blog-tag"></span>
    </div>
    <span id="category-count" class="category-count"></span>
  </div>
  <p><a class="blog-link" href="{{ '/categories/' | relative_url }}">返回分类列表</a></p>
  <ul id="category-posts" class="category-posts"></ul>
</section>

<script>
  (function () {
    const params = new URLSearchParams(window.location.search);
    const categoryName = params.get("name");
    const titleEl = document.getElementById("category-title");
    const badgeEl = document.getElementById("category-badge");
    const countEl = document.getElementById("category-count");
    const listEl = document.getElementById("category-posts");

    if (!categoryName) {
      titleEl.textContent = "未指定分类";
      if (badgeEl) badgeEl.remove();
      return;
    }

    fetch("{{ '/posts.json' | relative_url }}")
      .then((response) => response.json())
      .then((posts) => {
        const filtered = posts.filter((post) => (post.categories || []).includes(categoryName));
        titleEl.textContent = categoryName;
        if (badgeEl) badgeEl.textContent = categoryName;
        countEl.textContent = "共 " + filtered.length + " 篇";

        if (filtered.length === 0) {
          const item = document.createElement("li");
          item.textContent = "暂无文章。";
          listEl.appendChild(item);
          return;
        }

        filtered.forEach((post) => {
          const item = document.createElement("li");
          const link = document.createElement("a");
          const date = document.createElement("span");

          link.href = post.url;
          link.textContent = post.title;
          date.textContent = " " + post.date;

          item.appendChild(link);
          item.appendChild(date);
          listEl.appendChild(item);
        });
      });
  })();
</script>
