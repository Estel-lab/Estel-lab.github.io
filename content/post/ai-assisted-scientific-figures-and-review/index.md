---
title: "Rigor Boundaries in AI-Assisted Physics Workflows: Editable Vector Figures, Layout Auditing & Verifiable Peer Review"
date: 2026-11-10
summary: "Engineering guardrails for using AI in scientific writing, figure preparation, slide auditing, and peer review—without sacrificing physical accuracy or citation integrity."
tags:
  - AI for Science
  - Scientific Writing
  - Data Visualization
  - Peer Review
  - Research Workflow
---

AI coding and writing assistants can save enormous time across figure preparation, slide decks, manuscript revision, and peer review. Yet in physics and microelectronics, a single fabricated citation, misread plot curve, or rasterized figure text can undermine an entire paper. Over the past year, I distilled a set of **hard engineering boundaries** that let AI accelerate mechanical work while keeping scientific rigor non-negotiable.

---

### 1. Reproducing Plots from Raw Data: Never Confuse a Mean Curve with the Original Origin Project

When revisiting published or submitted device plots, a common mistake is taking raw `.mat` arrays, plotting their mean, and assuming it reproduces the paper figure. In reality, original **OriginPro (`.opju`)** projects encode critical plotting semantics—fitted trendlines, scaled error bands (e.g., $5\times$ standard deviation columns), axis transforms, and multi-sheet column links.

**Rule**: Before regenerating or modifying any scientific panel, audit both the numerical data and the exact plotting convention (fit vs. raw mean, error-bar definition, linear vs. log scale) against the source project.

---

### 2. Journal-Ready Figures & Physical Schematics

For journal submissions (such as *Nature*-family or *Applied Physics Reviews* guidelines), decoration is the enemy of clarity:
- **Vector & Editable Text**: Export clean vector graphics with white backgrounds, thin neutral black/gray axes, unified sans-serif typography (Arial/Helvetica), and embedded TrueType fonts—never outline-convert or rasterize axis labels.
- **Physically Accurate Schematics**: In electrical/optical setup diagrams, a single connector carrying two conductors (e.g., a BNC center pin + outer shield) must be drawn as one physical interface with two conductors—not two separate ports. Any unverified mechanical detail (such as chassis grounding continuity) is explicitly labeled *to be verified* rather than drawn as confirmed fact.

---

### 3. Automated Geometric Layout Auditing for Technical Slides

Relying on quick eyeball checks for 15–30 slide physics presentations inevitably misses overlapping kickers, clipped panel labels, or overflowing titles. Instead of manual inspection:
1. Render the generated `.pptx` to PDF via LibreOffice;
2. Run a geometric bounding-box intersection script (`audit_pdf_layout.py`) over all extracted PDF text boxes to automatically flag `text_overlap` and margin overflow;
3. For editable Word/PowerPoint equations, inspect and modify native **OMML (`<m:oMath>`)** XML structures directly instead of replacing formulas with plain text.

---

### 4. Verifiable Peer Review & Manuscript Revision Discipline

When using AI to assist with manuscript revisions or peer-review drafting:
- **Local-First Full-Text Parsing**: Convert the manuscript PDF locally via GPU MinerU (no cloud upload, original file untouched) so every equation, figure caption, and page number is checked verbatim.
- **Line-by-Line Traceability**: Every item in a Response Letter maps directly to the exact modified figure, table, or line number. Missing experimental data is **never fabricated**—gaps are marked explicitly as placeholders until measured.
- **Verified References Only**: Every suggested citation is cross-checked against local Zotero archives or Crossref/DOI metadata (title, authors, journal, year, DOI), and papers already cited in the manuscript are flagged for deeper discussion rather than duplicated.
