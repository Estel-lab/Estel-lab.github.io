---
title: "AI × Physics Research: Building a Two-Tier LLM Knowledge Base for Semiconductor & Quantum Optics"
date: 2026-11-18
summary: "How I combine curated Obsidian domain vaults with an agentic LLM wiki and resumable batch pipelines to synthesize 700+ physics papers without losing experimental rigor."
tags:
  - AI for Science
  - LLM Wiki
  - Semiconductor Physics
  - Quantum Optics
  - Research Workflow
---

Doing research across **narrow-bandgap semiconductor device physics** and **quantum optics experiments** means constantly switching between hundreds of journal papers, simulation scripts, device datasheets, and lab notebooks. Large language models can accelerate literature synthesis dramatically—*only* if the underlying knowledge architecture enforces strict provenance and separates experimental configurations from literature claims.

### 1. Two-Tier Knowledge Architecture
Rather than dumping everything into a single uncurated folder, I separate long-term physics knowledge from active agent memory:

- **Curated Domain Vaults (Obsidian)**: Dedicated vaults for semiconductor physics, SPDC quantum optics, and Zotero literature extractions, storing structured concept pages and immutable raw paper text.
- **Agentic LLM Wiki**: A lightweight four-layer workspace (`raw / meta / wiki / trajectories`) that mirrors compiled concept summaries from the domain vaults without duplicating raw full-text corpora. Successful multi-step analysis workflows are distilled into reusable case pages.

### 2. Preventing Hallucinated Physics: The `configured` Evidence Tier
A subtle failure mode when using AI in experimental physics is conflating *what the literature reports* with *what your own lab setup actually uses* (e.g., pump wavelength, crystal poling period, waveplate orientation, or doping profile). To solve this, our wiki schema introduces a dedicated **`configured`** evidence level:
- **Literature facts** (`measured`, `modeled`, `asserted`, etc.) describe the physical world and require citations.
- **`configured` facts** explicitly record user-selected apparatus and simulation parameters, preventing AI assistants from treating local design choices as universal physical laws.

### 3. Resumable Batch Synthesis of 700+ Papers
Processing hundreds of Zotero papers with an LLM often breaks midway due to network hiccups or interruptions. Using a durable SQLite-backed execution pipeline (`pi-durable`) with three layers of idempotency—deterministic `requestId` keys, append-only `progress.jsonl` checkpoints, and automatic `resume()` recovery—we batch-processed **703 extracted papers** at ~1.7–2.0 seconds per paper into structured summaries ready for cross-paper physics lookup.
