# Activity Log

> **Role of this file:** Append-only chronological record of all operations — ingests, queries, journal entries, CRM updates, and lint passes. Each entry uses a consistent prefix so it is parseable with simple tools.
>
> **Tip:** `grep "^## \[" log.md | tail -10` gives the last 10 entries.

---

## [2026-08-09] init | Second Brain Initialized

- **Action:** Repository initialized with base architecture.
- **Directories created:** `raw/`, `raw/processed/`, `raw/assets/`, `wiki/`, `journal/`, `CRM/`
- **Files created:** `index.md`, `log.md`, `agents.md`, `journal/index.md`, `CRM/index.md`
- **Schema:** `agents.md` populated with full system rules and custom workflows.

---

## [2026-08-09] ingest | Every Study Technique Explained in 18 Minutes

- **Source:** `raw/processed/Every Study Technique Explained in 18 Minutes.md`
- **YouTube Channel:** Justin Sung
- **Wiki pages created:** `Every-Study-Technique-Explained-in-18-Minutes`, `Schema-Building`, `Active-Recall`, `Feynman-Technique`, `Mind-Mapping`, `Spacing-Effect`, `Justin-Sung`
- **Wiki pages updated:** `Learning-Principles` (multi-source synthesis)
- **Key takeaways:** Justin Sung ranks 8 study techniques F→S tier. Schema building — forming connected knowledge networks — is the goal that separates S-tier from F-tier techniques. Mind mapping (done correctly) and AI-assisted Feynman technique are the gold standard.

## [2026-08-09] ingest | The Art of Becoming Dangerously Self-Educated

- **Source:** `raw/processed/The Art of Becoming Dangerously Self-Educated.md`
- **YouTube Channel:** Nextcore
- **Wiki pages created:** `The-Art-of-Becoming-Dangerously-Self-Educated`, `Self-Education`, `Primary-Sources`
- **Wiki pages updated:** `Learning-Principles`, `Feynman-Technique`, `Deep-Work` (multi-source)
- **Key takeaways:** Information access is no longer the bottleneck — understanding is. The 4-part self-education framework: try first (before you're ready), learn in public, go upstream to primary sources, embrace boredom.

## [2026-08-09] ingest | Why You Should Stop Watching YouTube (Yes, Even This Video)

- **Source:** `raw/processed/Why You Should Stop Watching YouTube (Yes, Even This Video).md`
- **YouTube Channel:** IIT-IIM Unfiltered
- **Wiki pages created:** `Why-You-Should-Stop-Watching-YouTube`, `Attention-and-Digital-Distraction`
- **Wiki pages updated:** `Learning-Principles`, `Deep-Work`, `Self-Education` (multi-source)
- **Key takeaways:** Even "productive" YouTube is avoidance if not implemented. The 85/15 rule: 85% of learning is doing. One second of social media costs 23 minutes of deep focus recovery. Structural elimination beats willpower.

## [2026-08-09] ingest | Download for Linux (Antigravity)

- **Source:** `raw/processed/Download for Linux.md`
- **Wiki pages created:** `Download-for-Linux-Antigravity`, `Antigravity`
- **Key takeaways:** Antigravity (Google) is installable on both deb and rpm Linux systems via official package repositories. Full install commands documented in wiki.

## [2026-08-09] ingest | LLM Wiki — Karpathy

- **Source:** `raw/processed/llm-wiki.md`
- **Wiki pages created:** `LLM-Wiki-Karpathy`, `Second-Brain-Architecture`, `Andrej-Karpathy`
- **Key takeaways:** Karpathy's foundational pattern: LLM incrementally builds a persistent, compounding wiki instead of re-deriving knowledge at query time. Three layers (raw, wiki, schema), three operations (ingest, query, lint). This vault is a direct implementation of this pattern.

---

## [2026-08-09] query | How to learn fast (tips & tricks)

- **Pages consulted:** `wiki/Learning-Principles.md`, `wiki/Schema-Building.md`, `wiki/Active-Recall.md`, `wiki/Feynman-Technique.md`, `wiki/Mind-Mapping.md`, `wiki/Deep-Work.md`, `wiki/Self-Education.md`
- **Answer filed back:** No (synthesis of existing notes)


