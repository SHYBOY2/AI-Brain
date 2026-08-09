---
title: "Cloud Second Brain Architecture"
tags: [source, second-brain, architecture, automation, antigravity, discord, obsidian-git]
created: 2026-08-10
updated: 2026-08-10
source_file: "raw/processed/‎Google Gemini 2.md"
source_url: "https://gemini.google.com/u/1/app/017f0da411ec1aae"
source_count: 1
sources:
  - "[[wiki/Cloud-Second-Brain-Pipeline-Setup]]"
  - "[[wiki/Second-Brain-Architecture]]"
---

# Cloud Second Brain Architecture

A clean architectural specification for the hybrid Second Brain system. This document describes the full design: a zero-cost pipeline bridging Discord (capture), Obsidian (local vault), Python automation (local processing), and Antigravity (LLM synthesis engine).

## Summary

This source is a structured architectural overview (not a step-by-step tutorial). It defines the five core objectives of the system, the 4-step operational loop, and the role of each technology component. Crucially, it distinguishes this system from a pure GitHub Actions approach: **Antigravity runs locally on the Lubuntu PC**, not on a remote cloud server.

## Key Takeaways

- **Antigravity is the local LLM engine**, not just an IDE. It acts as the synthesis agent that reads raw files, builds wiki pages, and manages the knowledge graph.
- **The 6-hour cron is local**, triggered by a background loop on the PC (not GitHub Actions). If the PC is sleeping, it catches up when it wakes.
- **Automatic model fallback:** If high-tier models (Gemini Pro, Claude) hit their 5-hour token reset limits, the system falls back to Gemini Flash automatically — no crashes.
- **Token efficiency is a first-class concern.** Web content is pre-parsed by the Obsidian Web Clipper or external tools *before* being handed to the LLM, so Antigravity only does high-level synthesis — not raw HTML scraping.
- **Multi-device sync via Obsidian Git** — wiki/ and journal/ directories are kept identical across the main PC, secondary PC, and phone.
- **Query interface via Discord:** Type `Query: What did I note about X?` in Discord → the local bot pipes it into Antigravity as `@wiki [Question]` → reply is posted back to Discord.

## The 5 Core Objectives

| # | Objective | Mechanism |
|---|-----------|-----------|
| 1 | Multi-device capture | Discord private channel as universal inbox |
| 2 | Voice memo support | Groq Whisper transcription |
| 3 | Token-optimized processing | Pre-parse content; LLM only synthesizes |
| 4 | Automated scheduling + fallback | Local 6-hour cron + model fallback logic |
| 5 | Universal knowledge retrieval | `Query:` prefix in Discord → Antigravity `@wiki` |

## The 4-Step Operational Loop

### Step 1: Frictionless Capture (Input)
- Phone/secondary PC → Discord `#ai-brain` channel
- Voice memos → Groq Whisper → text saved to `raw/`
- Links & text → saved directly to `raw/` or `journal/` with `📥` status

### Step 2: Automated Sweeps & Synthesis (Processing)
- 6-hour cron (local) triggers Antigravity
- Antigravity scans `raw/`, synthesizes structured wiki notes with frontmatter, moves sources to `processed/`

### Step 3: Local Storage & Syncing (The Vault)
- Antigravity writes to `wiki/` and `journal/` on the local machine
- Obsidian Git pushes/pulls to GitHub, syncing all devices

### Step 4: Real-Time Retrieval (Output)
- Type `Query:` in Discord → local bot → Antigravity `@wiki` → answer back to Discord

## Technology Stack

| Component | Role |
|-----------|------|
| **Discord** | Universal multi-device capture + query interface |
| **Obsidian** | Local visual knowledge base + markdown viewer |
| **Antigravity** | LLM synthesis engine (local, on-device) |
| **Obsidian Git** | Cross-device vault synchronization |
| **Groq Whisper** | Voice memo transcription |
| **Python** | Local automation scripts + Discord bot listener |

## Connections

- [[wiki/Cloud-Second-Brain-Pipeline-Setup]] — step-by-step setup guide for this architecture
- [[wiki/Second-Brain-Architecture]] — base wiki pattern this extends (Karpathy model)
- [[wiki/Discord-Bot-Obsidian-Integration]] — Discord bot technical details
- [[wiki/Antigravity]] — the LLM engine at the center of this system
