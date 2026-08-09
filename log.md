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

---

## [2026-08-10] ingest | Cloud Second Brain Pipeline Setup (Google Gemini conversation)

- **Source:** `raw/processed/‎Google Gemini.md` (+ `‎Google Gemini 1.md` — duplicate of same conversation)
- **Wiki pages created:** `Cloud-Second-Brain-Pipeline-Setup`, `Discord-Bot-Obsidian-Integration`, `GitHub-Actions-Automation`
- **Wiki pages updated:** `Second-Brain-Architecture` (added cloud extension section), `Antigravity` (added LLM engine role)
- **Key takeaways:** Full step-by-step setup guide: Discord bot creation, Groq API key, GitHub public repo, 3 secrets, deploy workflow + pipeline.py. Bot routes by message prefix: `Journal:` → journal/, `Query:` → Q&A + Discord reply, else → raw/ summarization. 6-hour cron via `0 */6 * * *`. Duplicate source (‎Google Gemini 1.md) archived alongside original.

## [2026-08-10] ingest | Cloud Second Brain Architecture (Google Gemini 2)

- **Source:** `raw/processed/‎Google Gemini 2.md`
- **Wiki pages created:** `Cloud-Second-Brain-Architecture`
- **Wiki pages updated:** `Second-Brain-Architecture`, `Antigravity`
- **Key takeaways:** Architectural spec defining 5 objectives and a 4-step operational loop (Capture → Process → Store/Sync → Retrieve). Antigravity runs locally as the LLM engine; GitHub Actions is one possible scheduler but local cron is also valid. Token efficiency is first-class: pre-parse content before LLM sees it. Model fallback (Gemini Flash) prevents crashes on quota limits.

## [2026-08-10] ingest | Obsidian AppImage Linux Fix (ChatGPT conversation)

- **Source:** `raw/processed/Cross-Device Agentic Workflow.md`
- **Wiki pages created:** `Obsidian-AppImage-Linux-Fix`
- **Wiki pages updated:** `Second-Brain-Architecture` (added cross-link to fix page)
- **Key takeaways:** AppImage installs of Obsidian don't register `.desktop` launchers automatically, breaking `obsidian://` protocol and Firefox Web Clipper. Fix: 4 bash commands to create the launcher, refresh the desktop DB, and register the protocol with xdg-mime. One-time permanent fix. Verified via `xdg-mime query default x-scheme-handler/obsidian`.

