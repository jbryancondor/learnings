---
source: https://www.augmentcode.com/guides/how-to-build-agents-md
date_accessed: 2026-04-04
published: 2025-06-01
author: Agentic AI Foundation & Tool Vendors
company: Linux Foundation / Agentic AI Foundation
level_mapping: [Level 3 - Context Engineering]
tags: [AGENTS.md, CLAUDE.md, configuration, standards, context-files]
agent: agent-5
---

## Summary
AGENTS.md and CLAUDE.md are context configuration files that provide instructions to AI coding agents. AGENTS.md is an open, tool-agnostic standard maintained by the Agentic AI Foundation (adopted 2025, 60,000+ repos). CLAUDE.md is Claude Code-optimized and supports Claude-specific features. Both provide a predictable location for context, rules, and project instructions. For multi-tool teams, symlink CLAUDE.md to AGENTS.md to keep files synchronized.

## Key Concepts
- **AGENTS.md**: Open standard for AI agent context (Linux Foundation / Agentic AI Foundation)
- **CLAUDE.md**: Claude Code-specific variant with support for Claude-specific features
- **Context File Purpose**: Single, predictable file replacing scattered documentation and implicit knowledge
- **Standardization**: 60,000+ GitHub repos using AGENTS.md as of 2025
- **Symlink Pattern**: For multi-tool teams, symlink files to prevent divergence
- **Size Management**: Start with one file; split at 150–200 lines for token budget reasons
- **Structure**: Project overview, agent instructions, context, tools, constraints, examples

## Quotes / Evidence
"AGENTS.md is an open, tool-agnostic standard for providing instructions to AI coding agents, stewarded by the Agentic AI Foundation under the Linux Foundation." — Official definition

"Think of AGENTS.md as a README for agents: a dedicated, predictable place to provide context and instructions." — Sourcegraph / OpenAI / Google / Cursor

"CLAUDE.md is Claude Code-optimized and differs by supporting Claude-specific features and richer contextual information." — Claude Code practice

## Related Terms
- Context Engineering
- Prompt Engineering
- Agent Framework
- System Prompts
- Memory Bank

## Relevance to Generative AI Engineer Role
You'll maintain AGENTS.md/CLAUDE.md as living documents that guide AI agents on your team's practices. These files become your interface to AI collaboration: instructions, constraints, tools, examples. They replace informal Slack conventions and scattered READMEs. Clear, concise context files dramatically improve agent quality and reduce hallucinations.

Sources:
- [Augment Code: How to Build AGENTS.md](https://www.augmentcode.com/guides/how-to-build-agents-md)
- [Complete Guide to CLAUDE.md and AGENTS.md](https://medium.com/data-science-collective/the-complete-guide-to-ai-agent-memory-files-claude-md-agents-md-and-beyond-49ea0df5c5a9)
- [Claude Lab: CLAUDE.md & AGENTS.md Guide](https://claudelab.net/en/articles/claude-code/claude-md-agents-md-complete-guide)
