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
        I am a PhD candidate in Microelectronics at HKUST(GZ), working on next-generation infrared photodetectors and single-photon characterization. My research centers on understanding and engineering avalanche carrier dynamics in narrow-bandgap semiconductors (particularly HgCdTe) through multi-scale simulation and experimental optics.

        - **Microscopic–Mesoscopic Device Simulation**: Developing custom C++ Monte Carlo frameworks coupled with TCAD/multiphysics modeling to bridge carrier scattering physics with macroscopic device performance—enabling **ultra-low-noise, high-bandwidth HgCdTe APDs** via electric field sculpting and acceleration meso-lattice (AML) regulation.
        - **Quantum Optics & SPDC Experiments**: Building and aligning a 405 nm pumped Type-II PPKTP polarization-entangled Sagnac photon-pair source with Time Tagger coincidence counting for photon-level characterization.
        - **Computational Optics & Novel Optoelectronics**: Exploring sparse sampling algorithms for wavefield reconstruction, 2D-material van der Waals contacts, and on-chip optoelectronic devices.

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
