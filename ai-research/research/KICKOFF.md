# Research Kickoff Prompt

> Copy everything below the line and paste it as your first message in the new session.

---

## PROMPT START

I am Bryan Condor, a software engineer learning to become a **Generative AI Engineer**. I have already done a planning phase in a previous session. You need to pick up from where we left off and execute the deep research plan.

---

## What was done in the previous session

1. Read the seed article: [The 8 Levels of Agentic Engineering](https://www.bassimeledath.com/blog/levels-of-agentic-engineering) by Bassim Eledath
2. Ran a preliminary research pass to validate and expand the plan
3. A UX Specialist and Expert Engineering Teacher collaborated to design a 3-part research plan
4. The plan went through 3 versions (v0 → v1 → v2)

The **active plan is v2**, located at:
```
/Users/bcondor/bcd/project/learnings/ai-research/research/plan-v2.md
```

The version index is at:
```
/Users/bcondor/bcd/project/learnings/ai-research/research/plan.md
```

---

## Your mission

**Read `plan-v2.md` first.** Then spawn 5 research agents in parallel to execute the research. Each agent owns a folder and a specific research thread.

---

## Research folder structure

All research output goes inside:
```
/Users/bcondor/bcd/project/learnings/ai-research/research/
```

Folder layout:
```
research/
├── plan.md                    ← version index
├── plan-v0.md                 ← archived
├── plan-v1.md                 ← archived
├── plan-v2.md                 ← ACTIVE PLAN — read this first
├── INDEX.md                   ← master index (agents must update this)
├── taxonomies/                ← Agent 1 output
├── company-cases/             ← Agent 2 output
├── tools-protocols/           ← Agent 3 output
├── orchestration-patterns/    ← Agent 4 output
└── terminology/               ← Agent 5 output
```

---

## File schema — every research file must follow this format

```markdown
---
source: <URL>
date_accessed: YYYY-MM-DD
published: YYYY-MM-DD
author: <name>
company: <company if applicable>
level_mapping: [3, 5]   # which of the 8 agentic levels this maps to
tags: [context-engineering, mcp, spotify]
agent: <agent-name>
---

## Summary
## Key Concepts
## Quotes / Evidence
## Related Terms
## Relevance to Generative AI Engineer Role
```

File names must be kebab-case slugs of the article title, e.g.:
- `spotify-honk-part-1-background-coding-agent.md`
- `context-engineering.md`
- `vibe-coding.md`

---

## The 5 research agents

Spawn all 5 in parallel. Each reads `plan-v2.md` for their full assignment (Part 3 of the plan).

---

### Agent 1 — Agentic Taxonomies & Competing Frameworks
**Output folder:** `taxonomies/`
**Mission:** Map and compare all agentic AI maturity models. There are at least 5 competing frameworks:
- Bassim Eledath's 8 Levels (the seed article)
- Steve Yegge's framework (referenced by Martin Fowler in March 2026 — URL unknown, search required)
- Microsoft Copilot Studio: L100–L500 model
- Nexocode: Crawl/Walk/Run/Scale
- Gartner: 5-stage Agentic AI Maturity Roadmap

**Confirmed sources to process:**
- https://www.bassimeledath.com/blog/levels-of-agentic-engineering
- https://martinfowler.com/fragments/2026-03-16.html
- https://martinfowler.com/articles/exploring-gen-ai/humans-and-agents.html
- https://learn.microsoft.com/en-us/microsoft-copilot-studio/guidance/maturity-model-overview
- https://nexocode.com/blog/posts/the-agentic-ai-maturity-model-crawl-walk-run-scale/
- https://arxiv.org/html/2505.10468v1

**Key searches:** "Steve Yegge agentic engineering framework 2025", "compound AI systems maturity model", "agentic AI taxonomy arxiv 2025 2026", "Forrester AI maturity model 2026"

**Priority:** Q4 2025 and 2026 sources first.

---

### Agent 2 — Company Case Studies
**Output folder:** `company-cases/`
**Mission:** Document real-world evidence of companies operating at specific agentic levels. Spotify is the primary target — they built "Honk", a background coding agent that produced 1,500+ merged PRs (Level 7 evidence).

**Confirmed sources to process (Tier 1 — all must be read):**
- https://engineering.atspotify.com/2025/11/spotifys-background-coding-agent-part-1
- https://engineering.atspotify.com/2025/11/context-engineering-background-coding-agents-part-2
- https://engineering.atspotify.com/2025/12/feedback-loops-background-coding-agents-part-3
- https://engineering.atspotify.com/2026/2/our-multi-agent-architecture-for-smarter-advertising
- https://addyosmani.com/blog/ai-coding-workflow/
- https://techcommunity.microsoft.com/blog/appsonazureblog/an-ai-led-sdlc-building-an-end-to-end-agentic-software-development-lifecycle-wit/4491896
- https://www.dawnliphardt.com/agentic-coding-spotifys-lessons-learned/
- https://departmentofproduct.substack.com/p/deep-how-spotify-is-using-ai-agents

**Key searches:** "Anthropic multi-agent production case study 2025 2026", "Cursor background agents production 2025", "GitHub Copilot Workspace real usage 2026", "Netflix Uber Airbnb AI agents engineering blog 2025 2026"

**Priority:** Q4 2025 and 2026 sources first.

---

### Agent 3 — Tools & Protocols Landscape
**Output folder:** `tools-protocols/`
**Mission:** Map every tool a Generative AI Engineer needs. Cover IDEs, CLIs, MCP ecosystem, SDD tools, memory systems, harness/observability tooling, rules file patterns.

**Confirmed sources to process:**
- https://martinfowler.com/articles/exploring-gen-ai/sdd-3-tools.html (SDD: Kiro, Spec-Kit, Tessl — Oct 2025)
- https://martinfowler.com/articles/exploring-gen-ai/context-engineering-coding-agents.html (Feb 2026)
- https://martinfowler.com/articles/exploring-gen-ai/harness-engineering-memo.html (Feb 2026)
- https://martinfowler.com/articles/exploring-gen-ai/partner-with-ai-and-throw-away-the-code.html (Jul 2025)
- https://martinfowler.com/articles/exploring-gen-ai/to-vibe-or-not-vibe.html (Sep 2025)
- https://martinfowler.com/articles/exploring-gen-ai/anchoring-to-reference.html (Sep 2025)
- https://github.com/github/spec-kit/blob/main/spec-driven.md
- https://www.thoughtworks.com/en-us/insights/blog/agile-engineering-practices/spec-driven-development-unpacking-2025-new-engineering-practices
- https://www.amplifilabs.com/post/agentic-mcp-copilot-rag-vibe-coding-and-the-language-of-modern-ai-development-the-definitive-glossary-of-ai-coding-terms
- https://thenewstack.io/memory-for-ai-agents-a-new-paradigm-of-context-engineering/

**Key searches:** "Model Context Protocol MCP ecosystem 2026", "Amazon Kiro SDD IDE review 2025", "Tessl AI IDE spec driven 2025", "Cursor vs Windsurf vs Claude Code 2026 comparison", "MemGPT Mem0 MemOS comparison 2025", "LangSmith Langfuse Helicone comparison 2025 2026", "MCPM MCP package manager"

**Priority:** Q4 2025 and 2026 sources first.

---

### Agent 4 — Orchestration & Background Agent Patterns
**Output folder:** `orchestration-patterns/`
**Mission:** Deep dive into multi-agent architecture patterns. Cover orchestration frameworks, design patterns, and new concepts introduced by Martin Fowler's 2026 entries.

**Confirmed sources to process:**
- https://martinfowler.com/articles/exploring-gen-ai/ccmenu-quality.html (Jan 2026)
- https://martinfowler.com/articles/exploring-gen-ai/humans-and-agents.html (Mar 2026)
- https://martinfowler.com/fragments/2026-03-16.html (Supervisory Engineering, Middle Loop — Mar 2026)
- https://engineering.atspotify.com/2026/2/our-multi-agent-architecture-for-smarter-advertising
- https://arxiv.org/html/2505.10468v1

**New concepts to research and document:**
- Supervisory Engineering / Middle Loop (Annie Vella, via Martin Fowler)
- Regenerative Architecture (Chad Fowler, via Martin Fowler)
- Evaluation over Review (Ankit Jain, via Martin Fowler)
- Plan-and-Execute pattern
- Orchestrator / Worker separation
- Implementer vs Reviewer agent separation (Bassim Eledath)
- LLM-as-Judge pattern
- A2A Protocol (Agent-to-Agent, Google → Linux Foundation AAIF Dec 2025)

**Key searches:** "LangGraph production patterns 2025 2026", "AutoGen multi-agent framework 2025", "CrewAI orchestration patterns 2026", "LLM as judge evaluation pattern 2025", "background agent dispatcher pattern", "A2A protocol agent to agent Google 2025"

**Priority:** Q4 2025 and 2026 sources first.

---

### Agent 5 — AI Terminology & Concepts Glossary
**Output folder:** `terminology/`
**Mission:** Define every key term in the Generative AI Engineer vocabulary. One file per term. Terms are ordered by learning progression — foundational terms first.

**46 terms to research and document (in this order):**

Foundation (learn first):
1. Tokenization / Token Budget
2. Context Window
3. Embeddings
4. Hallucination
5. Temperature / Top-p
6. System Prompt
7. Prompt Engineering
8. Few-shot / Zero-shot Prompting
9. Fine-tuning vs Prompting
10. Grounding

Level 1–2:
11. AI Pair Programming
12. Vibe Coding (coined by Andrej Karpathy, Feb 2025)
13. Vibe Coding Hangover
14. AI Fluency

Level 3:
15. Context Engineering
16. RAG (Retrieval-Augmented Generation)
17. Vector Database
18. AGENTS.md / CLAUDE.md
19. Memory Bank
20. Anchoring to a Reference Application

Level 4:
21. Compounding Engineering
22. SDD (Spec-Driven Development)
23. Spec-Kit (GitHub)
24. Amazon Kiro
25. Tessl

Level 5:
26. MCP (Model Context Protocol)
27. Tool Use / Function Calling
28. Skills (MCP Skills)
29. Agent Framework
30. Chain of Thought (CoT)
31. ReAct Pattern

Level 6:
32. Harness Engineering
33. Backpressure (AI systems)
34. LLM-as-Judge
35. Evaluation over Review
36. Compound AI Systems

Level 7:
37. Agentic Engineering
38. Background Agents
39. Orchestration
40. Autonomous Development Loop
41. Multi-Model Systems
42. Supervisory Engineering
43. Middle Loop

Level 8:
44. Regenerative Architecture
45. AI Alignment
46. MemOS

**Key searches per term:** Find the canonical source, original coinage/author, and best practical definition. Prioritize LinkedIn articles, engineering blogs, Andrej Karpathy posts, Simon Willison blog, swyx.io.

---

## Key context for all agents

- **The learner:** Bryan Condor, software engineer, goal = Generative AI Engineer
- **Seed article:** [8 Levels of Agentic Engineering](https://www.bassimeledath.com/blog/levels-of-agentic-engineering) — Bassim Eledath
- **Source priority rule:** 80%+ of sources must be from Q4 2025 or 2026
- **Most important author series:** Martin Fowler "Exploring Generative AI" — 25 articles (2023–2026), entries #18–#25 are mandatory
  - Full series index: https://martinfowler.com/articles/exploring-gen-ai.html
- **Spotify's agent is called "Honk"** — 3-part blog series Nov–Dec 2025 is the primary Level 7 evidence
- **Two key protocols to understand:** MCP (Anthropic, Nov 2024) and A2A (Google, 2025) — both now under Linux Foundation AAIF (Dec 2025)

---

## Success criteria

- [ ] At least 30 source articles researched across all agents
- [ ] 46 terminology entries defined (one file each, in learning progression order)
- [ ] Spotify Level 7 documented with all 4 primary sources
- [ ] All 5 competing maturity models compared in `taxonomies/`
- [ ] Steve Yegge's framework found and documented
- [ ] Martin Fowler Exploring GenAI #18–#25 all processed
- [ ] SDD tools (Kiro, Spec-Kit, Tessl) documented
- [ ] `INDEX.md` fully populated (one row per source file)
- [ ] 80%+ of sources from Q4 2025 or 2026

---

## INDEX.md format

Agents must maintain `/Users/bcondor/bcd/project/learnings/ai-research/research/INDEX.md`.
Each row = one source file. Format:

```markdown
# Research Index

| File | Title | Company | Date | Agent | Level | Tags |
|---|---|---|---|---|---|---|
| taxonomies/8-levels-agentic-engineering.md | The 8 Levels of Agentic Engineering | Independent | 2025 | agent-1 | 1-8 | taxonomy, maturity-model |
```

---

Now read `plan-v2.md`, then spawn the 5 agents in parallel and begin the research.

## PROMPT END
