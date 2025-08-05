---
title: Blog
summary: My courses
type: landing

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
