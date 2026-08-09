---
title: "Second Brain Architecture"
tags: [concept, knowledge-management, llm-wiki, obsidian, second-brain]
created: 2026-08-09
updated: 2026-08-10
source_count: 3
sources:
  - "[[wiki/LLM-Wiki-Karpathy]]"
  - "[[wiki/Cloud-Second-Brain-Pipeline-Setup]]"
  - "[[wiki/Cloud-Second-Brain-Architecture]]"
---

# Second Brain Architecture

The structural and operational design of this knowledge base, implemented from Karpathy's LLM Wiki pattern. This wiki *is* the implementation described in the foundational source.

## Three Layers

| Layer | Location | Owner | Rule |
|-------|----------|-------|------|
| Raw Sources | `raw/` | Human (curates) | Immutable — LLM reads, never writes |
| Wiki | `wiki/` | LLM (maintains) | LLM creates, updates, cross-references |
| Schema | `agents.md` | Co-evolved | Defines all conventions and workflows |

## How It Differs from RAG

**RAG (most AI tools):** Drop files → AI retrieves chunks at query time → generates answer → nothing persists.

**This wiki:** Sources are *compiled* into persistent, cross-linked pages. Synthesis already exists. Contradictions already flagged. Knowledge compounds with every addition.

## Navigation Files

- **`index.md`** — Content catalog. LLM reads this first at query time to find relevant pages.
- **`log.md`** — Append-only timeline. Format: `## [YYYY-MM-DD] <type> | <title>`

## Three Operations

1. **Ingest** — Source added to `raw/` → processed → wiki pages created/updated → source moved to `raw/processed/`
2. **Query** — Read index → drill into pages → synthesize with citations → file novel answers back
3. **Lint** — Periodic health check: orphans, contradictions, stale claims, gaps

## Custom Extensions in This Vault

Beyond Karpathy's base pattern, this vault adds:
- **Journal system** (`journal/`) — Personal entries triggered by "Journal" keyword
- **CRM system** (`CRM/`) — Contact records with alphabetical index
- **YouTube channel extraction** — Channel name added to frontmatter on ingest
- **Processed folder** (`raw/processed/`) — Source files moved here post-ingestion

## Cloud Extension (Hybrid Pipeline)

This vault has been extended with a cloud/local hybrid capture pipeline:
- **Discord** as a universal multi-device input interface
- **GitHub Actions** (or local cron) as the scheduled processing engine
- **Groq Whisper** for voice memo transcription
- **Antigravity** (local) as the LLM synthesis engine
- **Obsidian Git** for cross-device vault synchronization

See [[wiki/Cloud-Second-Brain-Architecture]] and [[wiki/Cloud-Second-Brain-Pipeline-Setup]] for full details.

## Tooling Notes

- **Obsidian** — The reading interface. Graph view reveals wiki shape and orphans.
- **Obsidian Web Clipper** — Converts web articles to markdown for `raw/`
- **`raw/assets/`** — Downloaded images stored here (Obsidian attachment folder setting)
- **Git** — Version control for the entire vault

## Related Pages

- [[wiki/LLM-Wiki-Karpathy]]
- [[wiki/Knowledge-Management]]
- [[wiki/Andrej-Karpathy]]
- [[wiki/Cloud-Second-Brain-Architecture]]
- [[wiki/Cloud-Second-Brain-Pipeline-Setup]]
- [[wiki/Discord-Bot-Obsidian-Integration]]
- [[wiki/GitHub-Actions-Automation]]
- [[wiki/Obsidian-AppImage-Linux-Fix]]
