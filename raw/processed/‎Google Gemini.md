---
title: "‎Google Gemini"
source: "https://gemini.google.com/u/1/app/db87786a01c1f469?is_sa=1&is_sa=1&android-min-version=301356232&ios-min-version=322.0&campaign_id=bkws&utm_source=sem&utm_medium=paid-media&utm_campaign=bkws&pt=9008&mt=8&ct=p-growth-sem-bkws&gclsrc=aw.ds&gad_source=1&gad_campaignid=20357620749&gclid=CjwKCAjwyuDTBhB-EiwANCQhLArTHTHxQSreg-7HQyGYCq1wiDiF_-Rkgh6_7WcgTIWHWAcnF3kaSxoCPAsQAvD_BwE&pageId=none"
author:
published:
created: 2026-08-10
description: "Meet Gemini, Google's AI assistant. Get help with writing, planning, brainstorming and more. Experience the power of generative AI."
tags:
  - "clippings"
---
add wiki of github and optimize the prompt without losing meaning and context too You are an AI systems auditor.

Goal:

Audit this repository to determine whether it functions like Andrej Karpathy's AI Second Brain / AI Knowledge Base. Use Andrej Karpathy's public AI Second Brain ideas and repository/wiki as the reference architecture where applicable.

Tasks:

1\. Inspect the entire repository.

2\. Determine whether the system implements:

\- Automatic knowledge ingestion

\- Markdown knowledge base

\- Bidirectional linking

\- Knowledge graph generation

\- Semantic retrieval

\- Hierarchical indexes

\- Cross-reference generation

\- Incremental indexing

\- Local-first workflow

\- AI-assisted note enrichment

\- Source attribution

\- Search and retrieval

\- Agent memory

\- Knowledge deduplication

3\. Compare the implementation against the expected architecture.

4\. For every missing or incomplete feature provide:

\- Feature

\- Current status

\- Why it matters

\- Files responsible

\- Exact files that must be modified

\- Recommended implementation

5\. Detect:

\- Broken links

\- Orphan notes

\- Isolated graph clusters

\- Duplicate notes

\- Empty indexes

\- Missing backlinks

\- Knowledge not reachable from index

6\. Evaluate the graph quality:

\- Density

\- Connectivity

\- Largest connected component

\- Number of orphan nodes

\- Link quality

\- Semantic quality

7\. Produce a final score (0–100):

Architecture:

Knowledge ingestion:

Knowledge graph:

Retrieval:

Automation:

Memory:

Overall:

Output only a concise Markdown report.

Do NOT rewrite code.

Do NOT modify files.

Do NOT explain your reasoning.

Keep the report under 800 words.

Here is the optimized prompt. I have streamlined the instructions to make them more impactful for the LLM, grouped related concepts for better AI comprehension, and seamlessly integrated the **GitHub Wiki** aspect into the reference architecture and markdown requirements.

**Role:** AI Systems Auditor

**Objective:** Audit this repository (including its GitHub Wiki structure) to evaluate its alignment with Andrej Karpathy's AI Second Brain / AI Knowledge Base concepts. Use his public repository, wiki, and ideas as the reference architecture.

**Tasks:**

**1\. Architecture & Feature Audit** Inspect the repository and its GitHub Wiki structure to determine the implementation status of:

- Automatic knowledge ingestion & deduplication
- GitHub Wiki-compatible Markdown knowledge base
- Bidirectional linking & cross-reference generation
- Knowledge graph generation & semantic retrieval
- Hierarchical indexes & incremental indexing
- Local-first workflow
- AI-assisted note enrichment & agent memory
- Source attribution & search/retrieval mechanics

**2\. Gap Analysis** For every missing or incomplete feature, provide a concise breakdown:

- **Feature:**
- **Current Status:**
- **Why it matters:**
- **Current Files:**
- **Files to Modify:**
- **Recommended Implementation:**

**3\. Data Integrity Detection** Identify and list occurrences of:

- Broken links or missing backlinks
- Orphan notes or isolated graph clusters
- Duplicate notes
- Empty indexes or knowledge unreachable from the main index

**4\. Graph Quality Evaluation** Evaluate the system's graph based on:

- Density & Connectivity
- Largest connected component
- Number of orphan nodes
- Link & Semantic quality

**5\. Final Scorecard (0–100)** Provide a score for the following categories:

- Architecture:
- Knowledge ingestion:
- Knowledge graph:
- Retrieval:
- Automation:
- Memory:
- **Overall:**

**Strict Output Constraints:**

- Output ONLY a concise Markdown report.
- Maximum length: 800 words.
- Do NOT rewrite code or modify files.
- Do NOT explain your reasoning; output only the requested report components.

### Why this is optimized:

- **Clarity & Token Efficiency:** Grouping the 14 individual features into logical pairs (e.g., "Knowledge graph generation & semantic retrieval") saves tokens and helps the AI process related concepts together.
- **GitHub Wiki Integration:** Specifically calls out "GitHub Wiki-compatible Markdown" and includes the Wiki in the initial inspection phase so the AI treats the Wiki as a core part of the architecture, not an afterthought.
- **Formatting:** Using bold headers and bullet points gives the AI a rigid structure to follow, which drastically improves the formatting of its output and ensures it adheres to the strict word count and "no explanation" constraints.

make it copy

```markdown
**Role:** AI Systems Auditor

**Objective:**
Audit this repository (including its GitHub Wiki structure) to evaluate its alignment with Andrej Karpathy's AI Second Brain / AI Knowledge Base concepts. Use his public repository, wiki, and ideas as the reference architecture.

**Tasks:**

**1. Architecture & Feature Audit**
Inspect the repository and its GitHub Wiki structure to determine the implementation status of:
- Automatic knowledge ingestion & deduplication
- GitHub Wiki-compatible Markdown knowledge base
- Bidirectional linking & cross-reference generation
- Knowledge graph generation & semantic retrieval
- Hierarchical indexes & incremental indexing
- Local-first workflow
- AI-assisted note enrichment & agent memory
- Source attribution & search/retrieval mechanics

**2. Gap Analysis**
For every missing or incomplete feature, provide a concise breakdown:
- **Feature:**
- **Current Status:**
- **Why it matters:**
- **Current Files:**
- **Files to Modify:**
- **Recommended Implementation:**

**3. Data Integrity Detection**
Identify and list occurrences of:
- Broken links or missing backlinks
- Orphan notes or isolated graph clusters
- Duplicate notes
- Empty indexes or knowledge unreachable from the main index

**4. Graph Quality Evaluation**
Evaluate the system's graph based on:
- Density & Connectivity
- Largest connected component
- Number of orphan nodes
- Link & Semantic quality

**5. Final Scorecard (0–100)**
Provide a score for the following categories:
- Architecture: 
- Knowledge ingestion: 
- Knowledge graph: 
- Retrieval: 
- Automation: 
- Memory: 
- **Overall:** 

**Strict Output Constraints:**
- Output ONLY a concise Markdown report.
- Maximum length: 800 words.
- Do NOT rewrite code or modify files.
- Do NOT explain your reasoning; output only the requested report components.
```

where his wiki link provide me his wiki github link

Andrej Karpathy didn't publish a full GitHub repository for his AI Second Brain wiki. Instead, he released the core architecture as a **GitHub Gist** (an "idea file" or schema) that you are meant to paste directly into an AI agent like Claude Code to generate and maintain the wiki locally.

Codersera

Here is the direct link to Karpathy's original Gist:

**[Andrej Karpathy's LLM Wiki Gist](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f)**

Codersera

If you are looking for complete, ready-to-use repositories where developers have implemented his exact method, here are a few popular community builds:

- **[danvega/karpathy-wiki](https://github.com/danvega/karpathy-wiki)**
	**:** A local CLI application using Spring AI agents to automate the ingestion and compilation of the wiki.
	GitHub
- **[agamarora/second-brain](https://www.google.com/search?q=https://github.com/agamarora/second-brain&authuser=1)**
	**:** A Claude Code-native template for managing a local Markdown knowledge base.
	GitHub
- **[charlie947/ai-second-brain](https://github.com/charlie947/ai-second-brain)**
	**:** A Claude Code skill packaging Karpathy's method.

add that into the prompt to

```markdown
**Role:** AI Systems Auditor

**Objective:**
Audit this repository (including its GitHub Wiki structure) to evaluate its alignment with Andrej Karpathy's AI Second Brain / AI Knowledge Base concepts. Use his public repository, wiki, and ideas (specifically referencing his core architecture Gist: https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f) as the reference architecture.

**Tasks:**

**1. Architecture & Feature Audit**
Inspect the repository and its GitHub Wiki structure to determine the implementation status of:
- Automatic knowledge ingestion & deduplication
- GitHub Wiki-compatible Markdown knowledge base
- Bidirectional linking & cross-reference generation
- Knowledge graph generation & semantic retrieval
- Hierarchical indexes & incremental indexing
- Local-first workflow
- AI-assisted note enrichment & agent memory
- Source attribution & search/retrieval mechanics

**2. Gap Analysis**
For every missing or incomplete feature, provide a concise breakdown:
- **Feature:**
- **Current Status:**
- **Why it matters:**
- **Current Files:**
- **Files to Modify:**
- **Recommended Implementation:**

**3. Data Integrity Detection**
Identify and list occurrences of:
- Broken links or missing backlinks
- Orphan notes or isolated graph clusters
- Duplicate notes
- Empty indexes or knowledge unreachable from the main index

**4. Graph Quality Evaluation**
Evaluate the system's graph based on:
- Density & Connectivity
- Largest connected component
- Number of orphan nodes
- Link & Semantic quality

**5. Final Scorecard (0–100)**
Provide a score for the following categories:
- Architecture: 
- Knowledge ingestion: 
- Knowledge graph: 
- Retrieval: 
- Automation: 
- Memory: 
- **Overall:** 

**Strict Output Constraints:**
- Output ONLY a concise Markdown report.
- Maximum length: 800 words.
- Do NOT rewrite code or modify files.
- Do NOT explain your reasoning; output only the requested report components.
```

also according to his video too https://www.youtube.com/watch?si=QTww-8QS-V4d5Lpj&v=yke4fLQUsh4&feature=youtu.be

Here is the updated and optimized prompt. I have incorporated the specific structural elements and workflow additions introduced in Matt Wolfe's video (Obsidian integration, the CRM, the Journaling engine, the `raw/` to `processed/` ingestion pipeline, and the `agents.md` configuration file) while maintaining the strict formatting rules.