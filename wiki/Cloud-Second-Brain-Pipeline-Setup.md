---
title: "Cloud Second Brain Pipeline Setup"
tags: [source, second-brain, discord, github-actions, groq, obsidian-git, automation]
created: 2026-08-10
updated: 2026-08-10
source_file: "raw/processed/‎Google Gemini.md"
source_url: "https://gemini.google.com/u/1/app/017f0da411ec1aae"
source_count: 1
sources:
  - "[[wiki/Cloud-Second-Brain-Architecture]]"
---

# Cloud Second Brain Pipeline Setup

A step-by-step walkthrough of setting up a zero-cost, cloud-based Second Brain pipeline using Discord as a universal capture inbox, GitHub Actions as the processing engine, Groq as the AI engine, and Obsidian as the local knowledge viewer.

## Summary

This source documents the full setup journey: creating a Discord bot, obtaining a Groq API key, creating a GitHub repository, storing secrets, and deploying two code files (`.github/workflows/second-brain.yml` and `scripts/pipeline.py`) to bring the automated pipeline online. The pipeline runs every 6 hours, processes Discord messages, and posts query answers back to Discord.

## Key Takeaways

- **Obsidian is the viewer; GitHub is the hard drive.** The master copy of the vault lives in a private GitHub repo. Obsidian Git syncs it locally.
- **Discord is the universal input device.** Voice memos, links, text, journal entries, and queries are all sent via a private Discord channel.
- **Groq handles transcription and LLM calls.** Whisper handles voice-to-text; `llama-3.3-70b-versatile` handles summarization and Q&A.
- **GitHub Actions is the free compute layer.** Public repos get unlimited free Actions minutes, enabling the 6-hour cron without any server.
- **The bot must register `Message Content Intent`** in the Discord Developer Portal — failing to save this causes a "blind bot" that cannot read messages.
- **Discord URL generator requires only the `bot` scope.** Checking extra scopes (like `email`) breaks the URL generation.
- **2-way Q&A:** Messages prefixed with `Query:` or `?` trigger the bot to read wiki pages and post the answer back to Discord.
- **Smart routing:** Messages prefixed with `Journal:` bypass summarization and are written directly to `journal/`.

## Setup Steps (Condensed)

### Phase 1: Discord Setup
1. Enable Developer Mode → copy Channel ID.
2. Create a Discord Application → create a Bot → copy Token.
3. Enable **Message Content Intent** and click **Save Changes**.
4. Use OAuth2 URL Generator → scope: `bot` only → invite to server.

### Phase 2: GitHub + Groq
1. Get a free Groq API key from `console.groq.com`.
2. Create a new **public** GitHub repository named `second-brain`.
3. Add three repository secrets: `DISCORD_BOT_TOKEN`, `DISCORD_CHANNEL_ID`, `GROQ_API_KEY`.

### Phase 3: Deploy Code
1. Create `.github/workflows/second-brain.yml` — cron schedule `0 */6 * * *`.
2. Create `scripts/pipeline.py` — handles Discord pull, link resolution, Whisper transcription, Groq summarization, query answering, and file management.
3. Trigger a manual run from the GitHub Actions tab to test.

## Pipeline Architecture

```
Discord Channel
      ↓
pipeline.py (GitHub Actions, every 6h)
      ├── pull_discord_updates()  — reads new messages, routes to raw/ or journal/
      ├── resolve_pending_links() — fetches YouTube transcripts & web articles
      ├── process_raw_files()     — summarizes via Groq, writes to wiki/
      └── rebuild_index()         — regenerates index.md from wiki/ frontmatter
```

## Related Pages

- [[wiki/Cloud-Second-Brain-Architecture]]
- [[wiki/Second-Brain-Architecture]]
- [[wiki/Discord-Bot-Obsidian-Integration]]
- [[wiki/Obsidian-AppImage-Linux-Fix]]
