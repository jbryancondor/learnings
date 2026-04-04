---
source: https://engineering.atspotify.com/2025/11/context-engineering-background-coding-agents-part-2
date_accessed: 2026-04-04
published: 2025-11-15
author: Spotify Engineering
company: Spotify
level_mapping: [3, 7]
tags: [spotify, honk, context-engineering, level-3, level-7, claude-code, prompt-engineering, tool-design]
agent: agent-2
---

## Summary

Part 2 of Spotify's Honk series dives into **context engineering** — how the team learned to guide background coding agents reliably across thousands of repositories. The core challenge: how do you tell an autonomous agent what to do at scale, without manual supervision? The article documents Spotify's evolution from open-source agents (Goose, Aider) through a homegrown loop to Claude Code, which became their top performer handling the **majority of production PRs** across ~50 migrations.

## Key Concepts

### Agent Evolution

| Stage | Agent | Outcome |
|---|---|---|
| Phase 1 | Open-source (Goose, Aider) | Failed to scale reliably across thousands of repos |
| Phase 2 | Homegrown loop | Better control but limited (10 turns, 3 retries); struggled with multi-file cascades |
| Phase 3 | Claude Code | Top performer; handles natural prompts, todo lists, spawns subagents |

### Six Context Engineering Best Practices

1. **Tailor to agent type** — Claude Code performs better with end-state descriptions than step-by-step instructions
2. **State preconditions** — explicitly specify when NOT to act (e.g., language constraints: "skip if not a Java repo")
3. **Use concrete code examples** — "before/after" code snippets heavily influence agent behavior
4. **Define verifiable goals** — test-driven objectives ("make these tests pass") outperform vague goals ("improve this code")
5. **One change per prompt** — multiple changes exhaust context window or yield partial results
6. **Request agent feedback** — agents effectively identify missing prompt information after execution (post-session debrief)

### Tool Design Philosophy

Spotify deliberately **limits tool access** to increase predictability:
- **Allowed**: Verify tool (formatters, linters, tests), Git (restricted subcommands, no push/origin), Bash allowlist (includes ripgrep)
- **Excluded**: Code search tools, documentation tools
- **Rationale**: "Fewer tools = higher predictability; less unpredictability sources; better testability"

### Static Prompts > Dynamic MCP

Spotify prefers large static prompts (version-controllable, testable) over dynamic MCP tool calls for most use cases. Trades flexibility for reliability.

## Quotes / Evidence

> "Claude Code: Top-performing agent — ~50 migrations, majority of production PRs merged"

> "Fewer tools = higher predictability" — Spotify's tool design philosophy

> "Agents effectively identify missing prompt information after execution" — post-session debrief pattern

> Boris Cherny (Anthropic): "The leading edge of how sophisticated engineering organizations are thinking about autonomous coding"

## Related Terms

- Context Engineering (Level 3)
- Background Coding Agents (Level 7)
- Claude Code
- Prompt engineering at scale
- Tool allowlisting
- Post-session debrief pattern
- End-state prompting vs. step-by-step prompting

## Relevance to Generative AI Engineer Role

Context Engineering is a first-class engineering discipline — not an afterthought. Key takeaways:

1. **Prompts are code** — version-control them, test them, treat failures as bugs. Spotify's preference for static prompts over dynamic MCP reflects this discipline.
2. **Tool design is agent design** — what tools you give an agent shapes its behavior as much as the model does. Fewer, well-defined tools beat broad access.
3. **The "end-state" prompting pattern** — for background agents, describe the desired final state rather than step-by-step instructions. This is a core technique to internalize.
4. **Agent selection matters** — Spotify tried Goose, Aider, homegrown solutions before Claude Code. Evaluating and selecting the right agent for your task is part of the job.
