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


- 2026-08-09 20:48 UTC | YouTube captured: `raw/2026-08-09-204807-yt-dSUfYAuc11E.md` (https://youtu.be/dSUfYAuc11E?si=fRwY2X2_X-gf_HXF)

- 2026-08-09 20:49 UTC | Processed `raw/2026-08-10-014657-note.md` → `wiki/2026-08-10-014657-note.md`

- 2026-08-09 20:49 UTC | Processed `raw/2026-08-10-015545-yt-7l6bXLAKyEI.md` → `wiki/2026-08-10-015545-yt-7l6bXLAKyEI.md`

- 2026-08-09 20:49 UTC | Processed `raw/2026-08-09-204807-yt-dSUfYAuc11E.md` → `wiki/2026-08-09-204807-yt-dSUfYAuc11E.md`

- 2026-08-09 20:49 UTC | Processed `raw/2026-08-10-014712-note.md` → `wiki/2026-08-10-014712-note.md`

- 2026-08-09 20:49 UTC | Query via Discord: `what is active recall` — answered

- 2026-08-09 20:51 UTC | YouTube captured: `raw/2026-08-09-205105-yt-OuByQWowjKA.md` (https://youtu.be/OuByQWowjKA?si=Gc3jGqJ5MaXnIrxV)

- 2026-08-09 20:51 UTC | YouTube captured: `raw/2026-08-09-205119-yt-BMcB7VwnQvI.md` (https://youtu.be/BMcB7VwnQvI?si=j4lBHOkIPXerrhED)

- 2026-08-09 20:51 UTC | YouTube captured: `raw/2026-08-09-205132-yt-jyLXcy5SGd8.md` (https://youtu.be/jyLXcy5SGd8?si=QWRnPwanWgYtBoae)

- 2026-08-09 20:51 UTC | YouTube captured: `raw/2026-08-09-205145-yt-O8_isifBeKk.md` (https://youtu.be/O8_isifBeKk?si=LEMPTJEznQjnEwcx)

- 2026-08-09 20:52 UTC | YouTube captured: `raw/2026-08-09-205203-yt-2ZgUTX3VNQ4.md` (https://youtu.be/2ZgUTX3VNQ4?si=ruqkFs7nWSL3Lvtq)

- 2026-08-09 20:52 UTC | YouTube captured: `raw/2026-08-09-205221-yt-kIw0YJ6YM58.md` (https://youtu.be/kIw0YJ6YM58?si=swEQEFHsigsDNyJm)

- 2026-08-09 20:52 UTC | YouTube captured: `raw/2026-08-09-205243-yt-bqFh1J1GEAY.md` (https://youtu.be/bqFh1J1GEAY?si=eqiWD4EQ95AhueRP)

- 2026-08-09 20:53 UTC | YouTube captured: `raw/2026-08-09-205305-yt-LQaEv6P4ooM.md` (https://youtu.be/LQaEv6P4ooM?si=NfA94m0OS0hZRyBo)

- 2026-08-09 20:53 UTC | YouTube captured: `raw/2026-08-09-205338-yt-wvaY5bG5p7A.md` (https://youtu.be/wvaY5bG5p7A?si=WjieQ4vhOSOWEJbl)

- 2026-08-09 20:53 UTC | Processed `raw/2026-08-09-205305-yt-LQaEv6P4ooM.md` → `wiki/2026-08-09-205305-yt-LQaEv6P4ooM.md`

- 2026-08-09 20:53 UTC | Processed `raw/2026-08-09-205221-yt-kIw0YJ6YM58.md` → `wiki/2026-08-09-205221-yt-kIw0YJ6YM58.md`

- 2026-08-09 20:53 UTC | Processed `raw/2026-08-09-205119-yt-BMcB7VwnQvI.md` → `wiki/2026-08-09-205119-yt-BMcB7VwnQvI.md`

- 2026-08-09 20:53 UTC | Processed `raw/2026-08-09-205203-yt-2ZgUTX3VNQ4.md` → `wiki/2026-08-09-205203-yt-2ZgUTX3VNQ4.md`

- 2026-08-09 20:53 UTC | Processed `raw/2026-08-09-205243-yt-bqFh1J1GEAY.md` → `wiki/2026-08-09-205243-yt-bqFh1J1GEAY.md`

- 2026-08-09 20:54 UTC | Processed `raw/2026-08-09-205145-yt-O8_isifBeKk.md` → `wiki/2026-08-09-205145-yt-O8_isifBeKk.md`

- 2026-08-09 21:00 UTC | Groq-processed `raw/2026-08-09-205338-yt-wvaY5bG5p7A.md` → `wiki/2026-08-09-205338-yt-wvaY5bG5p7A.md`

- 2026-08-09 21:00 UTC | Groq-processed `raw/2026-08-09-205132-yt-jyLXcy5SGd8.md` → `wiki/2026-08-09-205132-yt-jyLXcy5SGd8.md`

- 2026-08-09 21:02 UTC | Groq-processed `raw/2026-08-09-205105-yt-OuByQWowjKA.md` → `wiki/2026-08-09-205105-yt-OuByQWowjKA.md`

- 2026-08-09 21:06 UTC | YouTube captured: `raw/2026-08-09-210617-yt-dbDpegaaxvo.md` (https://youtu.be/dbDpegaaxvo?si=XGhm0ZeOVrBqjwXP)

- 2026-08-09 21:06 UTC | YouTube captured: `raw/2026-08-09-210637-yt-T88t25Lv82c.md` (https://youtu.be/T88t25Lv82c?si=gZ97FofUp1wJXa_3)

- 2026-08-09 21:06 UTC | YouTube captured: `raw/2026-08-09-210654-yt-C5OJJD3Eytk.md` (https://youtu.be/C5OJJD3Eytk?si=qQQ6nJhNgw0AKawp)

- 2026-08-09 21:07 UTC | YouTube captured: `raw/2026-08-09-210713-yt-SyzI0DpBBQI.md` (https://youtu.be/SyzI0DpBBQI?si=5AOtd227WBodLLcp)

- 2026-08-09 21:07 UTC | YouTube captured: `raw/2026-08-09-210731-yt-dap2O7RdLAI.md` (https://youtu.be/dap2O7RdLAI?si=YK5I41n2KmlHhAay)

- 2026-08-09 21:07 UTC | YouTube captured: `raw/2026-08-09-210747-yt-0CdE6oTkbj4.md` (https://youtu.be/0CdE6oTkbj4?si=-v4_rWnvGw7wM9Ff)

- 2026-08-09 21:07 UTC | YouTube captured: `raw/2026-08-09-210759-yt-Z26UeX13Hwk.md` (https://youtu.be/Z26UeX13Hwk?si=2__GcrhyUpipe7RC)

- 2026-08-09 21:08 UTC | YouTube captured: `raw/2026-08-09-210814-yt--d3icGN5xAM.md` (https://youtu.be/-d3icGN5xAM?si=ug5FGafgKJpqLrHl)

- 2026-08-09 21:08 UTC | YouTube captured: `raw/2026-08-09-210829-yt-GDMmxmn-p8I.md` (https://youtu.be/GDMmxmn-p8I?si=OcTbj1Io2W-Qy3EK)

- 2026-08-09 21:09 UTC | YouTube captured: `raw/2026-08-09-210901-yt-bwzK1FuSp1Q.md` (https://youtu.be/bwzK1FuSp1Q?si=mMhj16chGtJNCfvw)

- 2026-08-09 21:09 UTC | YouTube captured: `raw/2026-08-09-210925-yt-ffWSYAiHWJk.md` (https://youtu.be/ffWSYAiHWJk?si=WIYfY4WkoosMmiQi)

- 2026-08-09 21:09 UTC | YouTube captured: `raw/2026-08-09-210946-yt-XEmIlyJmVQo.md` (https://youtu.be/XEmIlyJmVQo?si=wwDfyMxU_tjOoACv)

- 2026-08-09 21:10 UTC | YouTube captured: `raw/2026-08-09-211006-yt-7-nak4BPZxg.md` (https://youtu.be/7-nak4BPZxg?si=7dA9XRvwMRDfu9P8)

- 2026-08-09 21:10 UTC | YouTube captured: `raw/2026-08-09-211023-yt-31bZOIk53_I.md` (https://youtu.be/31bZOIk53_I?si=IzV2G4nH-cpip1ch)

- 2026-08-09 21:10 UTC | YouTube captured: `raw/2026-08-09-211042-yt-KJ2Lvi9kG2Q.md` (https://youtu.be/KJ2Lvi9kG2Q?si=8GaGIAmUhSz7Mldz)

- 2026-08-09 21:10 UTC | YouTube captured: `raw/2026-08-09-211056-yt-uiNB-6SuqVA.md` (https://youtu.be/uiNB-6SuqVA?si=NvkSIvEKl8QVJbJ7)

- 2026-08-09 21:11 UTC | YouTube captured: `raw/2026-08-09-211109-yt-oBUhdwTt7ow.md` (https://youtu.be/oBUhdwTt7ow?si=HdrX0Oh07_okHGDT)

- 2026-08-09 21:11 UTC | Groq-processed `raw/2026-08-09-210814-yt--d3icGN5xAM.md` → `wiki/2026-08-09-210814-yt--d3icGN5xAM.md`

- 2026-08-09 21:12 UTC | Groq-processed `raw/2026-08-09-210637-yt-T88t25Lv82c.md` → `wiki/2026-08-09-210637-yt-T88t25Lv82c.md`

- 2026-08-09 21:12 UTC | Groq-processed `raw/2026-08-09-211042-yt-KJ2Lvi9kG2Q.md` → `wiki/2026-08-09-211042-yt-KJ2Lvi9kG2Q.md`

- 2026-08-09 21:14 UTC | Groq-processed `raw/2026-08-09-211006-yt-7-nak4BPZxg.md` → `wiki/2026-08-09-211006-yt-7-nak4BPZxg.md`

- 2026-08-09 21:16 UTC | YouTube captured: `raw/2026-08-09-211649-yt-yke4fLQUsh4.md` (https://youtu.be/yke4fLQUsh4?si=QTww-8QS-V4d5Lpj)

- 2026-08-09 21:31 UTC | YouTube captured: `raw/2026-08-09-Build-An-AI-Second-Brain-Knowledge-Base-Step-By-St.md` — "Build An AI Second Brain Knowledge Base (Step-By-Step)" (Matt Wolfe)
