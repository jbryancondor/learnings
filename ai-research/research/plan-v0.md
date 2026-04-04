# Generative AI Engineer — Deep Research Plan v0

**Created:** 2026-04-04
**Version:** 0 (initial strategy — before preliminary research)
**Goal:** Build a comprehensive, state-of-the-art knowledge base to become a Generative AI Engineer.
**Seed article:** [The 8 Levels of Agentic Engineering](https://www.bassimeledath.com/blog/levels-of-agentic-engineering)

---

## Research Structure

All findings are stored under this directory (`ai-research/research/`), organized by topic.

```
research/
├── plan-v0.md                       ← this file
├── plan-v1.md                       ← updated plan after preliminary research
├── INDEX.md                         ← master index of all sources (auto-updated)
├── taxonomies/                      ← Agent 1
│   └── <article-slug>.md
├── company-cases/                   ← Agent 2
│   └── <company-slug>.md
├── tools-protocols/                 ← Agent 3
│   └── <tool-slug>.md
├── orchestration-patterns/          ← Agent 4
│   └── <pattern-slug>.md
└── terminology/                     ← Agent 5
    └── <term>.md
```

### File schema (every research file)

```markdown
---
source: <URL>
date_accessed: YYYY-MM-DD
level_mapping: [1, 3, 5]   # which of the 8 agentic levels this maps to
tags: [context-engineering, mcp, spotify]
agent: <agent-name>
---

## Summary
## Key Concepts
## Quotes / Evidence
## Related Terms
## Relevance to Generative AI Engineer Role
```

---

## The 8 Levels of Agentic Engineering (Reference)

| Level | Name | Core Idea |
|---|---|---|
| 1 | Tab Complete | Copilot-style autocomplete |
| 2 | Agent IDE | Cursor-style multi-file AI editing |
| 3 | Context Engineering | Token optimization, system prompts, memory |
| 4 | Compounding Engineering | Plan→Delegate→Assess→Codify loop, rules files |
| 5 | MCP & Skills | Model Context Protocol, tools, APIs, CI pipelines |
| 6 | Harness Engineering | Observability, feedback loops, backpressure, security |
| 7 | Background Agents | Async multi-worker orchestration (Spotify) |
| 8 | Autonomous Agent Teams | Agent-to-agent coordination, no human loop |

---

## Agent Assignments

### Agent 1 — Agentic Taxonomies & Frameworks
**Output folder:** `taxonomies/`
**Mission:** Find papers, articles, and frameworks that define or extend the concept of agentic AI maturity in software engineering. Look for anything similar to the "8 levels" model.
**Key searches:**
- "levels of agentic engineering"
- "agentic AI maturity model software engineering"
- "AI coding agent taxonomy 2025 2026"
- "compound AI systems"
- arxiv papers on LLM agents in software engineering
- Google, Microsoft, OpenAI engineering blog posts on agent frameworks

---

### Agent 2 — Company Case Studies
**Output folder:** `company-cases/`
**Mission:** Find real-world evidence of companies operating at specific agentic levels. Prioritize Spotify (Level 7), Anthropic (16-agent C compiler), Cursor (hundreds of browser agents), GitHub Copilot evolution.
**Key searches:**
- "Spotify AI engineering agents 2025"
- "Spotify background agents level 7"
- "Anthropic multi-agent compiler"
- "Cursor autonomous agents browser"
- "GitHub Copilot Workspace"
- "enterprise AI agents production 2025 2026"
- LinkedIn engineering posts from Spotify, Anthropic, Google, Meta engineers

---

### Agent 3 — Tools & Protocols Landscape
**Output folder:** `tools-protocols/`
**Mission:** Map the current tooling landscape — what engineers actually use at each level. Cover MCP, Cursor, Claude Code, Windsurf, memory systems, CLAUDE.md / AGENTS.md patterns, harness/observability tooling.
**Key searches:**
- "Model Context Protocol MCP guide 2025"
- "Claude Code CLAUDE.md AGENTS.md patterns"
- "Cursor vs Windsurf vs Claude Code comparison"
- "MemGPT Mem0 memory systems LLM"
- "LLM observability tooling 2025"
- "context window management techniques"
- "harness engineering AI agents"

---

### Agent 4 — Orchestration & Background Agent Patterns
**Output folder:** `orchestration-patterns/`
**Mission:** Deep dive into how multi-agent systems are architectured. Cover orchestration frameworks, design patterns, and academic research.
**Key searches:**
- "LangGraph multi-agent orchestration"
- "AutoGen Microsoft multi-agent framework"
- "CrewAI agent orchestration"
- "ReAct reasoning acting LLM pattern"
- "chain of thought prompting"
- "LLM as judge pattern"
- "plan and execute agent pattern"
- "background agent dispatcher pattern"
- arxiv "multi-agent LLM systems 2025"

---

### Agent 5 — AI Terminology & Concepts Glossary
**Output folder:** `terminology/`
**Mission:** Surface, define, and explain every key term in the Generative AI Engineer vocabulary. Start with known terms, then discover new ones from articles found by other agents.
**Seed terms (known):**
- Vibe Coding
- Context Engineering
- AGENTS.md / CLAUDE.md
- Skills (MCP Skills)
- Memory Bank
- SDD (Spec-Driven Development)
- AI Fluency
- Prompt Engineering
- RAG (Retrieval-Augmented Generation)
- Agentic Engineering
- Background Agents
- Harness Engineering
- Backpressure (in AI systems)
- LLM-as-Judge
- Grounding
- Tool Use / Function Calling
- Few-shot / Zero-shot prompting
- Chain of Thought (CoT)
- ReAct Pattern
- Compound AI Systems
- AI Pair Programming
- Model Context Protocol (MCP)
- Autonomous Agents
- Orchestration
- System Prompt
- Temperature / Top-p
- Fine-tuning vs. Prompting
- AI Alignment
- Hallucination
- Tokenization / Token Budget

**Discover more terms** from: LinkedIn articles, Hacker News, Substack AI newsletters, engineering blogs
**Sources to check:** LinkedIn, Towards Data Science, The Pragmatic Engineer, Lenny's Newsletter, swyx.io, Simon Willison's blog

---

## Success Criteria

- [ ] At least 20 source articles researched across all agents
- [ ] At least 30 terminology entries defined
- [ ] Spotify Level 7 claim verified with a primary source
- [ ] Each of the 8 agentic levels has at least 2 supporting sources
- [ ] `INDEX.md` fully populated with all sources
- [ ] All files follow the standard schema

---

## Status

| Agent | Status | Files Created |
|---|---|---|
| Agent 1 — Taxonomies | `pending` | 0 |
| Agent 2 — Company Cases | `pending` | 0 |
| Agent 3 — Tools & Protocols | `pending` | 0 |
| Agent 4 — Orchestration Patterns | `pending` | 0 |
| Agent 5 — Terminology | `pending` | 0 |
