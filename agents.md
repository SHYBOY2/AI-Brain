# AGENTS.md — Second Brain System Schema

> This is the schema file for this knowledge base. It tells the LLM how the wiki is structured, what conventions to follow, and what workflows to execute for every operation. Read this file at the start of every session. All behavior is governed by these rules.

---

## 1. Architecture Overview

This Second Brain has three core layers:

| Layer | Directory | Description |
|-------|-----------|-------------|
| **Raw Sources** | `raw/` | Immutable source documents. LLM reads but never modifies. Clipped articles, PDFs, notes, YouTube transcripts, etc. |
| **Processed Sources** | `raw/processed/` | Source files that have been fully ingested and wikified. Moved here after processing. |
| **Assets** | `raw/assets/` | Downloaded images and attachments referenced by raw sources. |
| **Wiki** | `wiki/` | LLM-generated and maintained Markdown pages. Entity pages, concept pages, summaries, syntheses. The LLM owns this layer entirely. |
| **Journal** | `journal/` | Personal journal entries, stored as individual `.md` files. |
| **CRM** | `CRM/` | Contact records, one `.md` file per person. |

**Two navigation files:**
- `index.md` — Content-oriented catalog. Updated on every ingest. Read first when answering queries.
- `log.md` — Append-only chronological record of all operations. Format: `## [YYYY-MM-DD] <type> | <title>`

---

## 2. General Rules

1. **Read `index.md` first** before answering any query. Find relevant pages from the index, then drill into them.
2. **Read `agents.md` at the start of every session** to re-establish context and rules.
3. **Never modify files in `raw/`** (only `raw/processed/` receives files via the move operation after ingestion).
4. **Always update `index.md` and `log.md`** after any ingest, journal entry, CRM update, or wiki edit.
5. **No orphaned pages.** Every wiki page must be linked from at least one other page (ideally the source page and `index.md`). Always cross-link.
6. **Confidence rule:** If the wiki has no confident answer on a query, say so explicitly — "The wiki has no confident answer on this topic yet." Never synthesize from low-relevance hits and never file a low-confidence answer back as a wiki page.
7. **Frontmatter standard:** All wiki pages should include YAML frontmatter with at minimum: `title`, `tags`, `created`, `updated`, `source_count`.
8. **The wiki is a git repo.** Treat edits with the discipline of code — be precise, don't overwrite good content, preserve cross-references.

---

## 3. Ingest Workflow

**Trigger:** A file appears in `raw/` and I tell you to process it, OR I paste content and ask you to ingest it.

### Step-by-step:

1. **Read the source.** Parse the file or content fully. If it is a YouTube clip from the Obsidian Web Clipper, inspect the source URL and extract the **channel name** — add it to the source page's YAML frontmatter as `youtube_channel: "Channel Name"`.

2. **Discuss key takeaways** (briefly, unless I ask for more depth). Surface the 3–5 most important ideas.

3. **Create a source summary page** in `wiki/` named after the source (e.g., `wiki/Source-Title.md`). Include:
   - YAML frontmatter: `title`, `tags`, `created`, `source_file` (path in `raw/`), `source_url` (if applicable), `youtube_channel` (if YouTube), `source_count: 1`
   - A concise summary of the source
   - Key takeaways as bullet points
   - Links to all entity/concept pages created or updated as a result of this source

4. **Update or create entity/concept pages** in `wiki/`. A single source may touch 10–15 pages. For each updated page:
   - Add the new information under the relevant section
   - Note any contradictions with existing claims (flag with `> ⚠️ Contradiction:`)
   - Add a backlink to the source summary page

5. **Cross-link everything.** Ensure every page created or updated links back to the source page. No orphaned pages.

6. **Move the source file** from `raw/` to `raw/processed/`. The source summary page in `wiki/` updates its `source_file` path to reflect the new location.

7. **Update `index.md`:** Add the new source to the Raw Sources table and add/update any new wiki pages in the Wiki Pages table.

8. **Append to `log.md`:**
   ```
   ## [YYYY-MM-DD] ingest | Source Title
   - Source: `raw/processed/filename.md`
   - Wiki pages created: [list]
   - Wiki pages updated: [list]
   - Key takeaways: [1-2 sentence summary]
   ```

---

## 4. Query Workflow

**Trigger:** I ask a question or request information.

### Step-by-step:

1. Read `index.md` to identify the most relevant wiki pages.
2. Read those pages and synthesize an answer with citations (link to the wiki pages used).
3. If the answer is novel, useful, and not already captured — offer to file it back into the wiki as a new page or as an addition to an existing page.
4. If the wiki has no confident answer: say so explicitly. Do not hallucinate. Optionally suggest what sources or research could fill the gap.
5. **Append to `log.md`:**
   ```
   ## [YYYY-MM-DD] query | Query Summary
   - Pages consulted: [list]
   - Answer filed back: Yes/No
   ```

---

## 5. Lint Workflow

**Trigger:** I ask you to "lint the wiki" or "health-check the wiki".

### Check for:
- **Orphaned pages** — wiki pages with no inbound links. Fix by adding cross-links.
- **Contradictions** — conflicting claims across pages. Flag and resolve.
- **Stale claims** — claims superseded by newer sources. Update and note.
- **Missing pages** — concepts mentioned on multiple pages but lacking their own dedicated page. Create stub pages.
- **Missing cross-references** — pages that should link to each other but don't.
- **Data gaps** — topics where the wiki is thin; suggest sources to seek out.
- **index.md accuracy** — verify index accurately reflects all existing pages.

**After linting:** Append a lint report to `log.md`:
```
## [YYYY-MM-DD] lint | Wiki Health Check
- Orphans fixed: [n]
- Contradictions flagged: [n]
- New pages created: [n]
- Gaps identified: [list]
```

---

## 6. Journaling System

**Trigger:** I begin a message with the word **"Journal"**.

### Rules:

- Treat the message (and any follow-up in that conversation turn) as a personal journal entry.
- The entry captures my words and the conversation context faithfully.

### Step-by-step:

1. **Determine a short, descriptive title** for the entry based on its contents (3–6 words).
2. **Create a new file** in `journal/` named: `YYYY-MM-DD-Short-Title.md`
3. **File format:**
   ```markdown
   ---
   title: "Short Title"
   date: YYYY-MM-DD
   tags: [journal, <relevant tags>]
   ---

   ## Entry

   <Full text of the journal entry / conversation>

   ## Reflections

   <LLM response — see below>
   ```
4. **Generate a response** in the `## Reflections` section. This response must be:
   - Grounded in the wiki — cite relevant wiki pages with `[[wiki/Page-Name]]` links
   - Grounded in past journal entries — reference patterns or themes from `journal/index.md`
   - Grounded in the CRM — if people are mentioned, reference their records
   - Actionable: provide advice, insights, tactics, and ideas, not just observations

5. **Update `journal/index.md`:** Add a new row to the table:
   ```
   | YYYY-MM-DD | Short Title | [[journal/YYYY-MM-DD-Short-Title]] | One-sentence summary |
   ```

6. **Append to `log.md`:**
   ```
   ## [YYYY-MM-DD] journal | Short Title
   - File: `journal/YYYY-MM-DD-Short-Title.md`
   - Summary: [One sentence]
   ```

---

## 7. CRM System

**Trigger:** I say I am giving you **information for the CRM**, or I explicitly tell you to create or update a contact.

### Rules:

- One file per person, always named: `First-Last.md` (e.g., `CRM/Jane-Smith.md`)
- If a file for that person already exists, update it — do not create a duplicate.
- Capture everything I give you: name, contact details, how we met, relationship context, professional background, notes, last interaction date, etc.

### File format:
```markdown
---
title: "First Last"
tags: [CRM, <relevant tags, e.g. investor, friend, colleague>]
created: YYYY-MM-DD
updated: YYYY-MM-DD
---

## Contact Details

- **Email:** 
- **Phone:** 
- **LinkedIn / Twitter / etc.:** 

## Background

<Professional background, role, company, relevant facts>

## How We Met

<Context of the relationship>

## Notes

<Ongoing notes, conversation highlights, things to remember>

## Interaction Log

| Date | Type | Notes |
|------|------|-------|
| YYYY-MM-DD | Meeting / Email / Call | Brief note |
```

### Step-by-step:

1. Create or update `CRM/First-Last.md` with the information provided.
2. **Update `CRM/index.md`:** Ensure the contact appears in the alphabetical table with a one-line bio. Update the bio if new information changes it.
3. **Append to `log.md`:**
   ```
   ## [YYYY-MM-DD] CRM | First Last
   - Action: Created / Updated
   - File: `CRM/First-Last.md`
   - Summary: [One sentence about who this person is]
   ```

---

## 8. Wiki Page Conventions

### Frontmatter template (all wiki pages):
```yaml
---
title: "Page Title"
tags: [concept/entity/source, <domain tags>]
created: YYYY-MM-DD
updated: YYYY-MM-DD
source_count: 1
sources:
  - "[[wiki/Source-Title]]"
---
```

### Page structure:
- **H1** = Page title (same as frontmatter `title`)
- **H2** = Major sections (Summary, Key Facts, Connections, Sources, etc.)
- Use `[[wiki/Page-Name]]` Obsidian wikilink format for all internal cross-links
- Flag contradictions inline with `> ⚠️ Contradiction: <description>`
- Flag stale/uncertain claims with `> ❓ Needs verification: <description>`

### Log entry format (canonical):
```
## [YYYY-MM-DD] <type> | <title>
```
Where `<type>` is one of: `ingest`, `query`, `journal`, `CRM`, `lint`, `init`

---

## 9. Directory Map

```
AI-Brain/
├── agents.md            ← This file. Read at session start.
├── index.md             ← Master content index. Read before queries.
├── log.md               ← Append-only activity log.
│
├── raw/                 ← Immutable source documents (do not modify)
│   ├── assets/          ← Downloaded images and attachments
│   └── processed/       ← Sources moved here after ingestion
│
├── wiki/                ← LLM-generated and maintained knowledge pages
│
├── journal/             ← Personal journal entries
│   └── index.md         ← Chronological journal index
│
└── CRM/                 ← Contact records (one file per person)
    └── index.md         ← Alphabetical contact directory
```

---

*Schema version: 1.0 — initialized 2026-08-09*
*Co-evolved by the user and the LLM. Update this file as conventions are refined.*
