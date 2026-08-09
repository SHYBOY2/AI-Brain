---
title: "Antigravity"
tags: [entity, software, google, tool, second-brain]
created: 2026-08-09
updated: 2026-08-10
source_count: 2
sources:
  - "[[wiki/Download-for-Linux-Antigravity]]"
  - "[[wiki/Cloud-Second-Brain-Architecture]]"
---

# Antigravity

A software package by Google, available via official apt and rpm package repositories. Installation instructions exist for both deb-based (Debian, Ubuntu) and rpm-based (Red Hat, Fedora, SUSE) Linux distributions.

## Installation

See: [[wiki/Download-for-Linux-Antigravity]] for full installation commands.

**Quick reference:**
- deb: `sudo apt install antigravity`
- rpm: `sudo dnf install antigravity`

Repository keys and source configurations must be added first (see source page for full steps).

## Role in Second Brain

In the hybrid Second Brain pipeline, Antigravity serves as the **local LLM synthesis engine**:
- Scans the `raw/` folder every 6 hours (via local cron)
- Reads pre-parsed markdown (from Web Clipper or Discord)
- Synthesizes dense, interlinked wiki notes with proper frontmatter
- Handles query answering via `@wiki` context
- Falls back to secondary models (e.g., Gemini Flash) if token limits are hit

This is distinct from GitHub Actions — Antigravity runs **on-device** on the Lubuntu PC, not in the cloud.

## Related Pages

- [[wiki/Download-for-Linux-Antigravity]]
- [[wiki/Cloud-Second-Brain-Architecture]]
- [[wiki/Cloud-Second-Brain-Pipeline-Setup]]
