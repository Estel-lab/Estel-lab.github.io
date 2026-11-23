---
title: "AI × Physics Research: Building a Two-Tier LLM Knowledge Base for Semiconductor & Quantum Optics"
date: 2026-11-18
summary: "How I combine curated Obsidian domain vaults, an agentic LLM wiki with apparatus-fact grading, and a resumable SQLite batch pipeline to synthesize 700+ physics papers without losing experimental rigor."
tags:
  - AI for Science
  - LLM Wiki
  - Semiconductor Physics
  - Quantum Optics
  - Research Workflow
---

Working simultaneously on **narrow-bandgap semiconductor device simulation** and **quantum-optics experiments** creates a classic knowledge-management bottleneck: hundreds of journal articles, Sellmeier dispersion scripts, device datasheets, and lab notebooks live across disconnected folders. LLMs can dramatically speed up cross-paper synthesis and experimental troubleshooting—but only if the underlying knowledge architecture enforces **strict source provenance** and prevents AI from conflating local lab configurations with universal physics.

---

### 1. Why a Two-Tier Architecture Beats a Single Giant Folder

Dumping raw papers, scratch notes, and AI-generated summaries into one vault quickly degrades retrieval quality. Instead, we split knowledge into two layers with clear ownership:

| Layer | Role | Contents & Rules |
|---|---|---|
| **Curated Domain Vaults (Obsidian)** | Long-term, human-curated physics reference | Separate vaults by domain (`semiconductor`, `SPDC`, `Zotero` literature extractions); immutable `.raw/` paper texts + structured concept pages |
| **Agentic LLM Wiki** | Active cross-session working memory | Four-layer layout (`raw / meta / wiki / trajectories`); mirrors only compiled concept pages from domain vaults (never raw full texts) to keep search fast and high-signal |

A key advantage of the `trajectories` layer is **workflow distillation**: when a multi-step derivation, numerical audit, or troubleshooting sequence succeeds, the tool-call trace can be distilled into a reusable skill/case page rather than lost in chat history.

---

### 2. Solving a Subtle AI-for-Physics Failure: The `configured` Evidence Tier

When an AI assistant reads mixed lab notes and published papers, it frequently makes a dangerous category error: treating *your specific apparatus choices* (e.g., 405 nm pump wavelength, chosen PPKTP poling period, waveplate orientation, or simulated HgCdTe doping profile) as if they were universal literature claims—or conversely flagging your intentional design choices as "unverified assertions."

To eliminate this ambiguity, our wiki schema introduces a dedicated sixth evidence tier: **`configured`**.

- **World-description tiers** (`measured`, `modeled`, `asserted`, etc.) describe physical reality and must carry verifiable citations or experimental logs.
- **`configured`** strictly describes *what the researcher chose to build or simulate*. It requires no external citation, but must be updated whenever the physical apparatus or simulation geometry changes.

This single schema distinction makes AI-assisted physics Q&A dramatically cleaner and safer.

---

### 3. Durable Batch Synthesis of 703 Zotero Papers

Running an LLM over hundreds of extracted physics papers sequentially in a naive loop almost always fails halfway due to transient network errors or process restarts, leading to duplicate API costs or corrupted state.

Using a durable SQLite-backed execution harness (`pi-durable`), we structured batch literature extraction around **three layers of idempotency**:

1. **Deterministic `requestId` Keys**: Each paper is submitted with `item:<key>` as an idempotency key so retries retrieve the existing submission instead of re-billing.
2. **Write-Ahead `progress.jsonl`**: Structured outputs (`{id, answer, at}`) are flushed to disk before advancing, allowing completed items to be skipped instantly on restart.
3. **Automatic `harness.resume()`**: If a run is killed mid-turn, pending turns in `batch.sqlite` resume cleanly without losing in-flight work.

In practice, this pipeline processed **703 extracted Zotero papers** at **~1.7–2.0 seconds per paper** into structured summaries ready for cross-paper device-physics and quantum-optics retrieval.

---

### 4. Guardrails That Keep AI Useful in Real Physics

- **Never fabricate numbers or citations**: Every quantitative claim used in papers, CVs, or proposals is traced back to an extracted source paper or verified via Crossref/DOI metadata.
- **Registry-first lookup**: Query structured page registries rather than blindly grepping raw corpora, keeping context focused and token-efficient.
- **Keep raw sources immutable**: Always preserve original PDFs and extracted text untouched, storing AI-synthesized interpretations in clearly separated `wiki/` layers.
