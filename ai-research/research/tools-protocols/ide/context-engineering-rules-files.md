---
source: https://martinfowler.com/articles/exploring-gen-ai/context-engineering-coding-agents.html
date_accessed: 2026-04-04
published: 2026-02-05
author: Birgitta Böckeler
company: Thoughtworks
level_mapping: [3]
tags: [context-engineering, claude-md, agents-md, cursorrules, mem0, memgpt, rules-files, level-3]
agent: agent-3a
---

## Summary

Level 3 — Context Engineering — is the discipline of curating what a coding agent sees so it produces better results. While Level 2 tools provide the agentic execution engine, Level 3 determines what persistent knowledge, instructions, and conventions the agent operates with. This is where teams encode organizational standards, project conventions, and workflow guardrails into files that agents load automatically.

Core artifact types:
- **CLAUDE.md** — Claude Code's project instruction file (always auto-loaded)
- **AGENTS.md** — cross-tool standard instruction file (Sourcegraph/Linux Foundation initiative)
- **.cursorrules** — Cursor's project-scoped rules file
- **Mem0, MemGPT** — dynamic/persistent memory systems for agents beyond single sessions

## Key Concepts

### The Core Definition
> "Context engineering is curating what the model sees so that you get a better result." — Bharani Subramaniam (cited by Böckeler, 2026)

The key insight: **intelligence is not the bottleneck — context is.** Models are capable; what limits them is what they know about your specific project, team conventions, and organizational context.

### CLAUDE.md
- File placed in project root (or any directory); automatically read by Claude Code at session start
- Purpose: Project-wide conventions, architectural decisions, workflow rules, security constraints
- Scope: Hierarchical — root CLAUDE.md + subdirectory CLAUDE.md files (path-based scoping)
- **Critical insight**: As of 2026, CLAUDE.md is treated as foundational as `.gitignore` — non-optional for serious projects
- Content best practices:
  - Architecture rules (folder structure, naming conventions)
  - Tech stack constraints (no bundlers, pure HTML/CSS)
  - Security guidelines (no API keys, SRI for CDN scripts)
  - Workflow instructions (how to add new features, testing requirements)
  - What NOT to do (equally important as what to do)

Example structure (from this repo's AGENTS.md):
```
# Learnings Monorepo — Agent Guidelines
## What this repo is
## Architecture rules
## UI Guidelines
## Deployment rules
## Security
## What NOT to do
```

### AGENTS.md
- Cross-tool standardization initiative (mid-2025)
- Founded by: Sourcegraph, OpenAI, Google, Cursor, and others; maintained by Agentic AI Foundation under Linux Foundation
- **Pitch**: One file, any agent — single instruction file readable by Claude Code, Cursor, GitHub Copilot, Gemini CLI, Windsurf, Aider, Zed, Warp, RooCode
- Relationship to CLAUDE.md: CLAUDE.md can `@include` AGENTS.md (as this repo does via `@AGENTS.md` in CLAUDE.md)
- Enables: Write instructions once → works across all agentic tools the team uses

### .cursorrules
- Cursor-specific rules file at project root
- Similar purpose to CLAUDE.md but only read by Cursor
- Content: Coding style, framework preferences, file structure conventions, patterns to follow/avoid
- Status 2026: Being superseded by AGENTS.md standard in multi-tool teams; Cursor also reads AGENTS.md

### Claude Code Context Configuration System (Full)

| Feature | Type | When Loaded | Use Case |
|---------|------|-------------|----------|
| CLAUDE.md | Guidance | Always | Project-wide conventions |
| Rules | Guidance | Path-based | Scoped, modular guidance |
| Skills | Mixed | LLM/Human trigger | Lazy-loaded resources and procedures |
| Subagents | Instructions + Config | LLM/Human trigger | Parallelizable tasks |
| MCP Servers | Programs | LLM | API/tool access |
| Hooks | Scripts | Lifecycle events | Deterministic automation |
| Plugins | Distribution | Custom | Team sharing |

### Context Balance Problem
**Critical warning**: More context is not always better. Böckeler (2026) notes:
- Effectiveness decreases with excessive context (context stuffing)
- At 70% context window: Claude starts losing precision
- At 85%: Hallucinations increase
- At 90%+: Responses become erratic
- Transparency tools essential for understanding what's in context

### Memory Systems: Mem0 and MemGPT
- **Mem0**: Persistent memory layer for AI agents; stores user preferences, project facts, past decisions across sessions; provides relevance-scored recall
- **MemGPT**: OS-inspired virtual context management; manages main context + external memory banks; enables infinite context by swapping memory in/out like virtual memory pages
- Use case: When project knowledge exceeds single CLAUDE.md / AGENTS.md files; for long-running agent workflows; for personalization across sessions

### Spotify's Context Engineering at Scale (Nov 2025)
From Spotify's "Honk" background coding agent (Max Charas & Marc Bruggmann):
- Claude Code was their top-performing agent
- Context engineering principles discovered:
  1. **Tailor to agent type**: Claude Code performs better with outcome-focused vs step-by-step instructions
  2. **State preconditions**: Explicitly specify when NOT to act
  3. **Use concrete examples**: Code samples heavily influence results
  4. **Define verifiable endpoints**: Tests provide measurable goals
  5. **Single changes**: Combining multiple modifications exhausts context windows
  6. **Solicit feedback**: Agents can diagnose prompt deficiencies

## Quotes / Evidence

> "Claude is already smart enough — intelligence is not the bottleneck, context is. Every organization has unique workflows, standards, and knowledge systems, and Claude does not inherently know any of these." — 2026 practitioner consensus

> "CLAUDE.md is no longer optional — it is as important as your .gitignore." — Community consensus, 2026

> "AGENTS.md emerged in mid-2025 from a collaboration between Sourcegraph, OpenAI, Google, Cursor, and others, and is now maintained by the Agentic AI Foundation under the Linux Foundation. The pitch is simple: one file, any agent." — Data Science Collective, 2026

> "As long as LLMs are involved, we can never be certain of anything — probability-based thinking required despite configuration capabilities." — Birgitta Böckeler, 2026

> "Context effectiveness depends on similarity between sharer and receiver; iterative building superior to upfront copying." — Böckeler, 2026 (on sharing context files across teams)

> "Their deep understanding of prompt engineering and context management represents the leading edge of how sophisticated engineering organizations are thinking about autonomous coding." — Boris Cherny, Anthropic (on Spotify's Honk team)

## Related Terms

- **Context window** — the total tokens an LLM can process at once; everything the agent "sees"
- **Few-shot prompting** — providing examples in context to guide output format/style
- **In-context learning** — model adapts behavior based on examples within the prompt (no fine-tuning)
- **Rules file** — generic term for CLAUDE.md / AGENTS.md / .cursorrules
- **Hooks** — shell scripts that run on Claude Code lifecycle events (tool calls, session start, etc.)
- **MCP (Model Context Protocol)** — Anthropic's standard for connecting agents to external data sources
- **Skills** — Claude Code's lazy-loaded procedure files (`.claude/skills/`)
- **Subagents** — isolated Claude Code instances with their own context and tool permissions
- **Context stuffing** — anti-pattern of including too much in context, degrading model quality

## Relevance to Generative AI Engineer Role

Level 3 is where a Generative AI Engineer moves from **using** AI tools to **configuring** them for team-wide reliability. This is a high-leverage skill — a well-crafted CLAUDE.md multiplies the effectiveness of every team member using Claude Code.

Key competencies:
1. **Writing effective CLAUDE.md files**: Architecture rules, security constraints, workflow instructions, what-not-to-do sections
2. **AGENTS.md strategy**: Deciding what goes in AGENTS.md (cross-tool) vs CLAUDE.md (Claude-specific) vs .cursorrules (Cursor-specific)
3. **Context budget management**: Knowing what to include vs exclude; monitoring context saturation
4. **Memory architecture**: Choosing between CLAUDE.md (static), Mem0 (dynamic), MCP servers (live data) based on information volatility
5. **Skill development**: Writing reusable `.claude/skills/` procedures for team workflows

For Bryan Condor's transition: this repo already demonstrates Level 3 maturity — CLAUDE.md `@includes` AGENTS.md, both files are detailed and specific, and the skill system (`.claude/skills/`) is actively used. The next step is to understand the underlying principles to apply them in new contexts.
