---
source: https://www.bassimeledath.com/blog/levels-of-agentic-engineering
date_accessed: 2026-04-04
published: 2026-03-12
author: Bassim Eledath
company: Independent
level_mapping: [1, 2, 3, 4, 5, 6, 7, 8]
tags: [taxonomy, maturity-model, agentic-engineering, software-engineering, levels]
agent: agent-1
---

## Summary

Bassim Eledath's "8 Levels of Agentic Engineering" is the **anchor framework** for this research sprint. It defines a progression from basic autocomplete (Level 1) through fully autonomous agent teams (Level 8), framing each level as a qualitative shift in how software engineers interact with AI. The framework is practitioner-oriented — grounded in real tooling (Cursor, Claude Code, MCP) rather than abstract enterprise maturity.

## Key Concepts

### The 8 Levels

1. **Tab Complete** — Copilot-style autocomplete. Passive assistance, no agentic behavior.
2. **Agent IDE** — IDE-integrated chat tools (Cursor, Windsurf). Plan mode for multi-file edits, but context limitations constrain usefulness.
3. **Context Engineering** — Optimizing information density in prompts. "Every token needs to fight for its place." Includes `.cursorrules`, system prompts, tool descriptions, conversation history management.
4. **Compounding Engineering** — Plan-delegate-assess-codify loop. Practitioners update documentation (e.g., `CLAUDE.md`) with lessons learned, creating cumulative improvement across sessions. Named after Kieran Klaassen's concept.
5. **MCP & Skills** — Extending LLM capabilities via Model Context Protocol and custom skills. Agents access databases, APIs, CI pipelines, testing frameworks. Block's internal skills marketplace has 100+ skills with version control.
6. **Harness Engineering** — Building environments where agents self-verify through automated testing, linting, and observability. Key concept: "backpressure" — automated constraints preventing agents from becoming "slop machines."
7. **Background Agents** — Agents running asynchronously while humans focus elsewhere. Orchestrator patterns (e.g., "Dispatch" tool) manage multiple workers in parallel, using different models for different tasks.
8. **Autonomous Agent Teams** — Multi-agent coordination without a central orchestrator. Still experimental — Claude Code's Agent Teams, Anthropic's compiler-building agents show promise but reveal challenges in regression prevention.

### Cross-Cutting Themes

- **The Multiplayer Effect**: Team output depends heavily on the least advanced member. Progress bottlenecks at the lowest-level teammate.
- **Plan Mode Evolution**: "Plan mode is dying" as models improve — but remains essential without foundational work at Levels 3–6.
- **Model Separation Principle**: Never let the same model instance implement and review its own work — bias prevents honest self-assessment.
- **CLI > MCP for efficiency**: CLI tools increasingly replace MCPs for token efficiency — agents run targeted commands rather than injecting full schemas.

## Quotes / Evidence

- "Every token needs to fight for its place" (on context engineering)
- "Your output depends more than you'd think on the level of your teammates" (multiplayer effect)
- "Plan mode is dying" (on evolving model capabilities)
- Backpressure concept: automated constraints prevent agents from becoming "slop machines"

## Related Terms

- Context engineering, compounding engineering, harness engineering
- MCP (Model Context Protocol), skills marketplace
- Background agents, agent orchestration
- Ralph loop pattern, agentic flywheel

## Relevance to Generative AI Engineer Role

This is the primary framework for understanding where a Gen AI engineer should invest skill-building. Levels 3–6 represent the current high-leverage zone: context engineering, compounding documentation, MCP/skills development, and harness construction. Levels 7–8 are the near-future frontier where orchestration and multi-agent coordination become the core engineering discipline.
