---
title: "LLM Wiki Audit"
tags: [concept, architecture, audit, second-brain, llm-wiki]
created: 2026-08-10
updated: 2026-08-10
source_count: 0
sources: []
---

# Architectural Audit: The Anti-Gravity Project vs. Karpathy's LLM Wiki

This document provides a deep architectural and philosophical audit comparing your current operational structure (The Anti-Gravity Project) against Andrej Karpathy's "LLM Wiki" blueprint. 

---

## 1. Core Principle Check

**Verdict: Identical Core Philosophy**

The fundamental philosophy of your Anti-Gravity Project perfectly mirrors Karpathy's vision. Karpathy's core argument is that standard RAG (Retrieve-Augmented Generation) is flawed because it forces the LLM to "rediscover" and synthesize knowledge from scratch on every single query. Instead, knowledge should be compiled once, cross-referenced, and stored persistently.

Your system achieves this entirely. By enforcing the rules laid out in your `agents.md`, your LLM acts as an active **knowledge archivist** rather than a passive search engine. When a source is ingested, the system extracts the key takeaways, synthesizes them into dedicated concept/entity pages, and explicitly links them together. When queried, it searches a pre-compiled, highly structured knowledge graph rather than raw text dumps. The knowledge in your system **compounds** over time, which is the defining characteristic of the LLM Wiki.

## 2. The Feature Audit (What we have that he has)

Your system contains a 1:1 mapping of every critical layer and feature proposed in Karpathy's original blueprint. You have successfully implemented the complete foundation:

*   **The Schema Layer (`agents.md`):** You have a robust, highly detailed schema file that dictates exactly how the LLM should behave, how frontmatter should be structured, and what workflows to execute.
*   **The Raw Sources Layer (`raw/`):** You maintain an immutable directory for source materials (clips, transcripts, articles). 
*   **The Wiki Layer (`wiki/`):** You have a dedicated space for LLM-generated, heavily cross-referenced Markdown files. 
*   **Indexing & Logging:** 
    *   **`index.md`:** You maintain a dynamic, content-oriented catalog updated upon every ingestion, acting as the primary entry point for queries.
    *   **`log.md`:** You maintain a strict, append-only chronological ledger of all system actions, making the system's history easily parseable.
*   **Maintenance Workflows:** Your `agents.md` defines explicit **Ingest**, **Query**, and **Lint** workflows, directly mapping to Karpathy's proposed maintenance loops (handling orphans, contradictions, and stale claims).

## 3. The Divergence Report (Where we are different)

While you have faithfully implemented the foundation, you have significantly expanded the scope of the system. Here is where the Anti-Gravity Project diverges from the original blueprint, and how those changes impact the system:

### A. The `processed/` Directory (State Management)
*   **The Divergence:** Karpathy's blueprint simply drops sources into `raw/`. You introduced a workflow where ingested files are moved to `raw/processed/`.
*   **The Impact:** This is a massive operational improvement. By treating `raw/` as a queue and `processed/` as an archive, you solved the state-management problem. This enables your automated Discord/GitHub pipeline (`capture_bot.py`) to run unattended cron jobs on the `raw/` folder without infinitely re-ingesting the same files. It enhances the architecture without breaking the "immutable raw source" rule.

### B. The `journal/` and `CRM/` Directories (Domain Expansion)
*   **The Divergence:** Karpathy's wiki focuses purely on objective knowledge compilation (articles, concepts, entities). You have introduced distinct, structured layers for personal time-series data (Journaling) and relational data (CRM).
*   **The Impact:** This transforms the project from a simple "encyclopedia" into a **Holistic Personal Operating System**. 
    *   The Journal workflow smartly requires the LLM to provide *Reflections* grounded in the Wiki and CRM, creating a feedback loop between objective knowledge and personal application.
    *   The CRM creates an entity-relationship model for humans, expanding the graph view.
    *   While divergent from a strict "knowledge wiki," these additions apply Karpathy's exact same philosophical engine (LLM-maintained markdown with a strict schema) to new data domains. 

### C. The Cloud/Discord Ingestion Pipeline
*   **The Divergence:** The original blueprint implies a mostly local, manual invocation of the LLM by the user. You have built an autonomous, multi-device pipeline using a Discord bot, Groq API, and automated background workers.
*   **The Impact:** You have solved the "friction of capture" problem. By allowing voice notes, URLs, and text to be sent via Discord and automatically synthesized in the background, you have made the LLM Wiki practical for mobile and daily use.

## 4. Conclusion

**Final Verdict:** The Anti-Gravity Project is a highly faithful, fully-featured implementation of the LLM Wiki concept, but it has evolved into something much more powerful.

You have not compromised any of Karpathy's core principles. The LLM still does the grunt work, the knowledge still compounds incrementally, and the markdown remains the ultimate source of truth. 

However, your recent changes—specifically the automated state-management (`processed/`), domain expansions (`journal/`, `CRM/`), and the Discord ingestion pipeline—have upgraded the system from a theoretical prototype into a **production-ready, automated Second Brain**. You took Karpathy's blueprint and successfully engineered the infrastructure required to actually live in it.
