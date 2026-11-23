---
title: "AI × Physics Literature: Local GPU Parsing of Formula-Heavy PDFs & Scanned Textbooks"
date: 2026-11-17
summary: "Benchmarks and lessons learned comparing local GPU MinerU against OCRmyPDF+EasyOCR on 700+ page semiconductor textbooks and technical standards."
tags:
  - AI for Science
  - PDF Parsing
  - MinerU
  - Semiconductor Physics
  - Local GPU
---

Semiconductor physics and analog circuit design rely heavily on classic scanned textbooks, national measurement standards, and formula-dense theses. Feeding raw scanned PDFs directly into LLMs fails immediately unless equations, tables, and multi-column layouts are faithfully converted into structured text.

### 1. Two Routes Evaluated on a Local RTX 4070 Ti SUPER (16 GB)
To keep all documents strictly local (no cloud upload, original PDFs preserved and SHA256-verified), we benchmarked two open-source pipelines on a **749-page scanned textbook** (*Design of Analog CMOS Integrated Circuits*) and a **797-page technical reference set** (HgCdTe detector measurement standards and dissertations):

| Pipeline | Output Format | Strengths | Limitations |
|---|---|---|---|
| **OCRmyPDF + EasyOCR (GPU)** | Searchable PDF (hidden text layer) | Preserves original scanned page pixels 1:1 (`PIXELS_IDENTICAL`) | High Chinese character error rate on dense/decorative fonts; equations & subscripts copy poorly |
| **Local GPU MinerU (window = 64 pages)** | Structured Markdown + JSON + figures | Preserves LaTeX equations, tables, and section hierarchy cleanly; ready for LLM Wiki ingestion | Reflowed Markdown rather than original page-image overlay |

### 2. Practical Throughput & Engineering Takeaways
- **Speed & VRAM**: On a local RTX 4070 Ti SUPER, MinerU processed **6 PDFs totaling 797 pages in ~3 minutes 20 seconds** using 64-page sliding batches, occupying ~8 GB VRAM.
- **Validate Before Scaling**: Always run a 10-page pilot first and verify page-index coverage (`0 .. N-1`) via structured metadata rather than trusting console logs.
- **Direct Bridge to AI Research**: Converting physics monographs and standards into clean LaTeX-aware Markdown unlocks accurate formula lookup, cross-referencing with simulation scripts, and fast ingestion into domain knowledge vaults.
