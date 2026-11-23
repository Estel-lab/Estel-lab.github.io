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
        我是香港科技大学（广州）微电子学博士研究生，研究围绕下一代红外光电探测器与单光子表征展开，重点结合多尺度器件仿真与光学实验，理解和调控窄带隙半导体（特别是碲镉汞 HgCdTe）中的雪崩载流子动力学。

        - **微观–介观器件物理仿真**：自主开发 C++ 微观–介观耦合蒙特卡洛框架，结合 TCAD 与多物理场仿真，通过电场雕塑与加速介观晶格（AML）调控，设计**超低噪声、高带宽红外雪崩光电二极管**。
        - **量子光学与 SPDC 实验**：搭建 405 nm 泵浦 Type-II PPKTP 偏振 Sagnac 纠缠光子源，开展光路精密对准与 Time Tagger 符合计数表征。
        - **计算光学与新型光电器件**：开展波场稀疏采样重建算法、二维材料范德华接触红外探测器及片上光电器件研究。

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
