---
# Leave the homepage title empty to use the site title
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
        text: Download CV
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
      title: 'Research'
      subtitle: ''
      text: |-
        I am a PhD candidate in Microelectronics at HKUST(GZ), working on next-generation infrared photodetectors. My research centers on understanding and engineering avalanche carrier dynamics in narrow-bandgap semiconductors, particularly HgCdTe, through multi-scale simulation approaches.

        I develop **microscopic-mesoscopic Monte Carlo frameworks** to bridge first-principles carrier scattering with macroscopic device performance. My work aims at designing **ultra-low-noise, high-bandwidth infrared avalanche photodiodes** through electric field sculpting and mesoscopic dynamics regulation.

        I am also interested in 2D-material-based optoelectronic devices, on-chip optical logic gates, and the intersection of computational physics with experimental device design.

        Please reach out to collaborate 😃
    design:
      columns: '1'
  - block: collection
    id: papers
    content:
      title: Featured Publications
      filters:
        folders:
          - publication
        featured_only: true
    design:
      view: article-grid
      columns: 2
  - block: collection
    content:
      title: Recent Publications
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
      title: News
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
      title: Talks
      filters:
        folders:
          - event
    design:
      view: article-grid
      columns: 1
---
