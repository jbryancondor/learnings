---
source: https://addyosmani.com/blog/ai-coding-workflow/
date_accessed: 2026-04-04
published: 2025-12-01
author: Addy Osmani
company: Google (Chrome)
level_mapping: [2, 3, 7]
tags: [google, addy-osmani, ai-coding-workflow, level-2, level-3, level-7, claude-code, copilot, cursor, cross-model-review]
agent: agent-2
---

## Summary

Addy Osmani (Chrome team, Google) documents a mature AI-assisted engineering workflow that spans Level 2 (Agent IDE), Level 3 (Context Engineering), and touches Level 7 (Background Agents). The article's most cited statistic: **~90% of Claude Code's own codebase is written by Claude Code itself** — cited from Anthropic. Osmani describes a workflow where AI is treated as a "powerful pair programmer that requires clear direction, context and oversight," not a replacement for engineering judgment.

## Key Concepts

### Core Workflow Principles

1. **Planning first** — brainstorm a detailed specification with the AI, then outline a step-by-step plan before writing any code. Prevents wasted cycles.
2. **Iterative chunking** — break projects into small tasks, tackle them one by one. Reduces LLM confusion from monolithic requests.
3. **Context provision** — use tools like `gitingest` and `repo2txt` to dump relevant codebase sections for the LLM. Context quality drives output quality.

### Tools Cited

| Tool | Role | Level |
|---|---|---|
| Claude Code | Primary agent IDE | 2, 7 |
| Copilot Agent | Background agent, PR creation | 7 |
| Jules (Google) | Background coding agent | 7 |
| Cursor | IDE assistant | 2 |
| Context7 | MCP for context management | 5 |
| Chrome DevTools MCP | Debugging integration | 5 |
| Gemini CLI | Command-line AI | 2 |

### Background Agent Behavior (Level 7)

Tools like Claude Code and Copilot Agent now work asynchronously:
> "Cloning your repo into a cloud VM and working on tasks in the background... opening a PR for you."

This is an explicit description of Level 7 behavior: the agent works independently, asynchronously, and delivers a pull request without the engineer watching each step.

### Cross-Model Review Pattern

Osmani recommends using **different AI models to review each other's work** — a novel quality assurance technique that uses model diversity to catch errors neither model alone would catch.

### Human Accountability

> "Never commit code you can't explain."
> "You are responsible for quality."
> "The developer remains the director of the show."

## Quotes / Evidence

> "~90% of the code for Claude Code is written by Claude Code itself" (Anthropic-sourced)

> "Treat the LLM as a powerful pair programmer that requires clear direction, context and oversight"

> "AI will happily produce plausible-looking code, but you are responsible for quality"

> "Cloning your repo into a cloud VM and working on tasks in the background...opening a PR for you."

## Related Terms

- Agent IDE (Level 2)
- Context Engineering (Level 3)
- Background Agents (Level 7)
- Cross-model review
- gitingest / repo2txt
- MCP (Context7, Chrome DevTools)
- Specification-first development

## Relevance to Generative AI Engineer Role

Osmani's workflow is a practitioner's guide from a senior engineer at a top tech company. Key takeaways:

1. **Specification-first is non-negotiable** — plan before coding with AI. The AI is most useful when it has a clear target.
2. **Cross-model review** is an underrated technique: using Claude to review GPT-4 output (and vice versa) surfaces errors each model's training biases would hide.
3. **The 90% statistic is the meta-point** — if Anthropic uses Claude Code to write most of Claude Code, this is the highest possible endorsement of agentic coding as production practice.
4. **Context tools are infrastructure** — gitingest, repo2txt, MCP integrations are the plumbing that makes AI useful at real project scale.
