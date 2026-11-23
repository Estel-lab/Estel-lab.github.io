---
title: "AI × Physics Literature: Local GPU Parsing of Formula-Heavy PDFs & Scanned Textbooks"
date: 2026-11-17
summary: "Hands-on benchmarks comparing local GPU MinerU against OCRmyPDF+EasyOCR on 797 pages of HgCdTe measurement standards/theses and a 749-page scanned analog CMOS textbook."
tags:
  - AI for Science
  - PDF Parsing
  - MinerU
  - Semiconductor Physics
  - Local GPU
---

Semiconductor device physics and analog circuit design rely heavily on scanned classic textbooks, national measurement standards, and equation-dense dissertations. Feeding raw scanned PDFs directly into an LLM fails immediately: without faithful extraction of LaTeX equations, subscripts, Greek symbols, and multi-column tables, AI assistants either hallucinate constants or silently skip derivations.

Because many lab references and dissertations should stay **strictly local** (no cloud upload, original PDFs untouched and SHA256-verified), we benchmarked two open-source GPU pipelines on a single workstation (**NVIDIA RTX 4070 Ti SUPER, 16 GB VRAM**).

---

### 1. Test Corpora

1. **HgCdTe Detector Testing Reference Set (797 pages across 6 PDFs)**: Includes national infrared detector measurement standards (GB/T 13584-2011, GB/T 17444-2013), weak-signal detection monographs (277 pages), and a doctoral dissertation (131 pages).
2. **Scanned Classic Textbook (749 pages)**: *Design of Analog CMOS Integrated Circuits* (2nd Ed., Chinese edition)—pure image scan with zero embedded text layer, dense circuit schematics, and mixed Chinese/English mathematical expressions.

---

### 2. Pipeline Comparison: Hidden Text Layer vs. Structured Markdown

| Dimension | OCRmyPDF + EasyOCR (GPU) | Local GPU MinerU (64-Page Window) |
|---|---|---|
| **Output Format** | Searchable PDF (original scan + invisible text layer) | Structured Markdown + JSON metadata + cropped figures |
| **Visual Fidelity** | **1:1 pixel-identical** to original scan (`PIXELS_IDENTICAL: True`) | Reflowed Markdown (does not overlay original page image) |
| **Equations & Tables** | Weak—subscripts, Greek letters, and fractions frequently break on copy | Strong—preserves LaTeX math (`formula_enable=True`) and structured tables (`table_enable=True`) |
| **Chinese Scan Accuracy** | Noticeable character errors on dense/stylized fonts (e.g., `CMOS` → `CNOS`) | Much cleaner layout & mixed-language segmentation for LLM ingestion |
| **Best Use Case** | Human reading & Ctrl+F browsing while keeping original typesetting | Feeding textbooks, standards, and theses directly into an **LLM Physics Knowledge Base** |

---

### 3. Local GPU Throughput & Engineering Lessons

On the RTX 4070 Ti SUPER (16 GB), batch-converting the **797-page technical reference set** with local MinerU (`window_size=64` pages per batch) achieved:

- **Total Wall-Clock Time**: **~3 minutes 20 seconds** from launch to completion across all 6 PDFs (e.g., 277 pages split cleanly into 5 batches).
- **Peak VRAM Usage**: **~8 GB** (~50% of 16 GB), leaving comfortable headroom without OOM crashes.

#### Four Practical Rules Before Running Full-Book Batches
1. **Run a 10-Page Pilot First**: Verify visual fidelity, equation formatting, and SHA256 immutability of the source PDF on pages 1–10 before committing a 700-page run.
2. **Check Structured Metadata, Not Console Logs**: On Windows GBK consoles, non-ASCII filenames often render garbled in terminal logs even when outputs are completely intact. Poll a structured `run_status.json` state file and verify full `0 .. N-1` page-index coverage in `pdf_info`.
3. **Diagnose Failure Layers Separately**: When OCR quality looks poor, separate **input scan quality** vs. **engine parameters** vs. **post-processing** on a single representative page rather than blindly re-running the entire book.
4. **Keep Outputs Isolated**: Store all converted Markdown and trial artifacts in dedicated sibling folders (`_mineru_md/`, `_easyocr_trial/`) so source archives remain pristine.
