---
title: "LLM Wiki — Karpathy"
tags: [source, reference, knowledge-management, llm-wiki, second-brain, andrej-karpathy]
created: 2026-08-09
updated: 2026-08-09
source_file: "raw/processed/llm-wiki.md"
source_url: "https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f"
source_count: 1
sources: []
---

# LLM Wiki — Karpathy

**Author:** Andrej Karpathy | **Type:** Foundational pattern document

## Summary

The original gist that inspired this Second Brain. Karpathy describes a pattern for building personal knowledge bases using LLMs — replacing ad-hoc RAG (retrieve-then-answer) with a persistent, compounding wiki that the LLM incrementally builds and maintains. The key insight: knowledge should be compiled once and kept current, not re-derived on every query.

> This wiki — the one you are currently reading — is a direct implementation of the pattern described here.

## Core Idea: Wiki vs. RAG

| Approach | Mechanism | Problem |
|----------|-----------|---------|
| RAG (NotebookLM, ChatGPT uploads) | Retrieve chunks → generate answer at query time | Rediscovers knowledge from scratch every time. No accumulation. |
| **LLM Wiki (this)** | Incrementally build & maintain a persistent wiki | Knowledge compiled once, cross-referenced, synthesis already exists. Compounds over time. |

## Three-Layer Architecture

1. **Raw Sources** (`raw/`) — Immutable source documents. LLM reads, never modifies.
2. **The Wiki** (`wiki/`) — LLM-generated markdown. The LLM owns this entirely.
3. **The Schema** (`agents.md`) — Configuration file defining conventions and workflows. Co-evolved by user and LLM.

## Three Operations

- **Ingest:** Drop source → LLM reads, discusses, writes summary page, updates entity/concept pages (may touch 10–15 pages), appends to log.
- **Query:** LLM reads index first, drills into pages, synthesizes answer with citations. Good answers are filed back as new wiki pages.
- **Lint:** Periodic health check — orphans, contradictions, stale claims, missing pages, data gaps.

## Indexing & Logging

- **`index.md`** — Content-oriented catalog. Updated on every ingest. Read first at query time.
- **`log.md`** — Append-only chronological record. Parseable with `grep "^## \[" log.md | tail -5`.

## Key Principles

- The human curates sources, asks questions, directs analysis. The LLM does all the bookkeeping.
- Good answers should be filed back as wiki pages — explorations compound just like ingested sources.
- The wiki is just a git repo of markdown files. Version history and collaboration for free.
- Related to Vannevar Bush's **Memex** (1945) — a personal, curated knowledge store with associative trails. The LLM solves the maintenance problem Bush couldn't.

## Tooling Mentioned

- **Obsidian Web Clipper** — Convert web articles to markdown for `raw/`.
- **Obsidian graph view** — Visualize wiki shape; identify hubs and orphans.
- **Marp** — Markdown-based slide decks from wiki content.
- **Dataview** — Obsidian plugin for querying page frontmatter dynamically.
- **qmd** — Local markdown search with BM25/vector hybrid (for when index.md isn't enough at scale).

## Related Wiki Pages

- [[wiki/Second-Brain-Architecture]] — Implementation details for this specific vault
- [[wiki/Knowledge-Management]] — Broader context and related systems
- [[wiki/Andrej-Karpathy]] — Author entity page
- [[wiki/Vannevar-Bush-Memex]] — Historical antecedent referenced in the gist
