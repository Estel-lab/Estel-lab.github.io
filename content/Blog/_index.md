---
title: Blog
summary: My Blogs
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
      title: Blog
      filters:
        folders:
          - Blog
    design:
      view: article-grid
      columns: 2
---
