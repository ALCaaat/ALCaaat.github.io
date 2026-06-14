# ALCaaat.github.io

这是一个使用 Jekyll 默认 `minima` 主题的 GitHub Pages 博客。

## 写文章

文章放在 `_posts/` 目录，文件名格式：

```text
YYYY-MM-DD-title.md
```

文章示例：

```markdown
---
layout: post
title: 文章标题
date: 2026-06-14 15:00:00 +0800
categories: [随笔]
---

正文内容。
```

## 放图片

图片按这个结构存放：

```text
img/年/月/日/文章/
```

例如：

```text
img/2026/06/14/hello/1.jpg
```

文章中引用：

```markdown
![图片说明](/img/2026/06/14/hello/1.jpg)
```

## 分类

文章 front matter 中写：

```yaml
categories: [随笔]
```

分类页会自动聚合到 `/categories/`。
