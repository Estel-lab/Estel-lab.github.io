---
title: 博客
summary: 我的博客
type: landing

view: card

cascade:
  - _target:
      kind: page
    params:
      show_breadcrumb: true

sections:
  - block: collection
    id: Blog
    content:
      title: 博客
      filters:
        folders:
          - Blog
    design:
      view: article-grid
      columns: 2
---
