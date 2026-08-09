---
title: "Discord Bot Obsidian Integration"
tags: [concept, discord, automation, second-brain, obsidian]
created: 2026-08-10
updated: 2026-08-10
source_count: 2
sources:
  - "[[wiki/Cloud-Second-Brain-Pipeline-Setup]]"
  - "[[wiki/Cloud-Second-Brain-Architecture]]"
---

# Discord Bot Obsidian Integration

How Discord is used as a universal, multi-device capture and query interface for the Second Brain, feeding into the local Obsidian vault via automation.

## Summary

Discord acts as the "inbox" of the Second Brain. Because Discord has native mobile and desktop apps, it becomes the easiest way to capture thoughts, links, and voice memos from any device without requiring the device to have direct access to the local vault.

## How It Works

### Capture (Input)
Send any of these to a private Discord `#ai-brain` channel:
- **Voice memo (.ogg)** → Groq Whisper transcription → saved to `raw/`
- **Text note** → saved to `raw/` with `type: text`
- **URL/Link** → saved to `raw/` with `type: link`; content fetched later
- **`Journal:` prefix** → bypasses summarizer → written directly to `journal/`
- **`Query:` or `?` prefix** → routes to query handler instead of ingestion

### Processing
- A Python bot (`pipeline.py`) polls the Discord channel for new messages.
- Messages are saved to `raw/` with a status flag (`raw`, `resolved`).
- On the next scheduled sweep, Antigravity processes raw files into wiki pages.

### Output (Query Mode)
- Send `Query: What do I know about X?` → bot reads wiki pages → formats an answer → posts it back to the same Discord channel.
- Works from phone, tablet, any device with Discord.

## Discord Bot Setup Requirements

| Requirement | Why |
|-------------|-----|
| Developer Mode ON | Needed to copy Channel ID |
| Message Content Intent ON | Without this, the bot cannot read message text |
| Scope: `bot` only in OAuth2 URL Generator | Adding extra scopes breaks the URL |
| Bot Token stored as GitHub/local secret | Authentication for API calls |

## Key Technical Details

- Discord API endpoint: `GET /api/v10/channels/{id}/messages`
- Bot uses `after` parameter to track last-seen message (stored in `.state/discord_offset.json`)
- Bot replies via: `POST /api/v10/channels/{id}/messages`
- Discord's 2000-character limit requires chunking long responses into 1900-char blocks

## Connections

- [[wiki/Cloud-Second-Brain-Pipeline-Setup]] — full setup guide
- [[wiki/Cloud-Second-Brain-Architecture]] — architectural overview
- [[wiki/Second-Brain-Architecture]] — base system this integrates with
