---
title: ""
date: 2022-10-24
type: landing

design:
  spacing: "6rem"

sections:
  - block: resume-biography-3
    content:
      username: admin
      text: ""
      button:
        text: 下载简历
        url: uploads/resume.pdf
    design:
      css_class: dark
      background:
        color: black
        image:
          filename: stacked-peaks.svg
          filters:
            brightness: 1.0
          size: cover
          position: center
          parallax: false
  - block: markdown
    content:
      title: '研究方向'
      subtitle: ''
      text: |-
        我是香港科技大学（广州）的微电子学博士研究生，致力于下一代红外光电探测器的研究。我的研究核心是通过多尺度仿真方法，理解和调控窄带隙半导体（特别是碲镉汞HgCdTe）中的雪崩载流子动力学。

        我开发**微观-介观蒙特卡洛框架**，桥接第一性原理载流子散射理论与宏观器件性能。我的工作目标是通过电场调控和介观动力学调节，设计**超低噪声、高带宽的红外雪崩光电二极管**。

        同时，我也对基于二维材料的光电器件、片上光学逻辑门，以及计算物理与实验器件设计的交叉领域感兴趣。

        欢迎合作交流 😃
    design:
      columns: '1'
  - block: collection
    id: papers
    content:
      title: 代表性论文
      filters:
        folders:
          - publication
        featured_only: true
    design:
      view: article-grid
      columns: 2
  - block: collection
    content:
      title: 近期论文
      text: ""
      filters:
        folders:
          - publication
        exclude_featured: false
    design:
      view: citation
  - block: collection
    id: news
    content:
      title: 学术动态
      subtitle: ''
      text: ''
      filters:
        folders:
          - post
    design:
      view: article-grid
      columns: 2
  - block: collection
    id: talks
    content:
      title: 会议报告
      filters:
        folders:
          - event
    design:
      view: article-grid
      columns: 1
---
