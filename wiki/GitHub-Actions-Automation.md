---
title: "GitHub Actions Automation"
tags: [concept, automation, github-actions, second-brain, ci-cd]
created: 2026-08-10
updated: 2026-08-10
source_count: 1
sources:
  - "[[wiki/Cloud-Second-Brain-Pipeline-Setup]]"
---

# GitHub Actions Automation

Using GitHub Actions as a free, serverless compute layer to run the Second Brain pipeline on a scheduled cron without owning or maintaining a server.

## Summary

GitHub Actions provides free CI/CD compute time for public repositories. This makes it possible to run the Second Brain pipeline (Discord polling → content resolution → LLM summarization → wiki updates) on a 6-hour cron schedule at zero cost.

## Key Facts

- **Free compute for public repos:** Public GitHub repositories get unlimited free Actions minutes.
- **Cron syntax for 6-hour schedule:** `cron: "0 */6 * * *"`
- **Manual trigger:** `workflow_dispatch: {}` allows clicking "Run workflow" from the Actions tab to test anytime.
- **Concurrency control:** Setting `cancel-in-progress: false` ensures no pipeline run is aborted mid-way.
- **Write permissions:** The workflow needs `permissions: contents: write` to commit wiki changes back.

## Workflow File Structure

```yaml
name: second-brain-pipeline

on:
  schedule:
    - cron: "0 */6 * * *"   # Every 6 hours
  workflow_dispatch: {}     # Manual trigger

concurrency:
  group: second-brain-pipeline
  cancel-in-progress: false

permissions:
  contents: write

jobs:
  process:
    runs-on: ubuntu-latest
    timeout-minutes: 8
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-python@v5
        with:
          python-version: "3.12"
      - run: pip install requests pyyaml trafilatura youtube-transcript-api
      - name: Run pipeline
        env:
          DISCORD_BOT_TOKEN: ${{ secrets.DISCORD_BOT_TOKEN }}
          DISCORD_CHANNEL_ID: ${{ secrets.DISCORD_CHANNEL_ID }}
          GROQ_API_KEY: ${{ secrets.GROQ_API_KEY }}
        run: python scripts/pipeline.py
      - name: Commit and push
        run: |
          git config user.name "second-brain-bot"
          git config user.email "actions@users.noreply.github.com"
          git add -A
          git diff --quiet --cached || git commit -m "chore: automated second brain sync"
          git push origin HEAD:main
```

## Secrets Required

| Secret Name | What It Is |
|------------|------------|
| `DISCORD_BOT_TOKEN` | Bot token from Discord Developer Portal |
| `DISCORD_CHANNEL_ID` | ID of the private Discord channel |
| `GROQ_API_KEY` | API key from console.groq.com |

## Connections

- [[wiki/Cloud-Second-Brain-Pipeline-Setup]] — full setup guide
- [[wiki/Cloud-Second-Brain-Architecture]] — architectural context
- [[wiki/Discord-Bot-Obsidian-Integration]] — what this pipeline processes
