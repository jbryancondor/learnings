---
source: https://support.claude.com/en/articles/12512176-what-are-skills
date_accessed: 2026-04-04
published: 2025-10-01
author: Anthropic
company: Anthropic
level_mapping: [Level 5 - MCP & Skills]
tags: [skills, Claude-skills, procedures, reusable, knowledge]
agent: agent-5
---

## Summary
Claude Skills are specialized procedures that activate dynamically when needed, providing procedural knowledge—instructions for how to complete specific tasks. Released in late 2025, skills teach Claude how to approach problems, complementing MCP's external tool integration. Anyone can create skills using Markdown; advanced skills include executable scripts. Skills live in `.claude/skills/` folders and work everywhere across Claude (claude.ai, Claude Code, API).

## Key Concepts
- **Procedural Knowledge**: Instructions for task completion, not just tool definitions
- **Markdown-Based**: Anyone can write skills; no coding required for simple ones
- **Executable Scripts**: Advanced skills support Python, Shell, or other executables
- **Dynamic Activation**: Skills load when relevant to the task at hand
- **Reusable Components**: Build once, use across projects
- **Complementary to MCP**: MCP = external tools; Skills = internal procedures
- **Folder Structure**: `.claude/skills/` for persistent, versioned skill storage
- **Plan Integration**: Available across Free, Pro, Max, Team, Enterprise

## Quotes / Evidence
"Skills provide specialized procedures that activate dynamically when needed, providing procedural knowledge—instructions for completing specific tasks." — Claude documentation

"MCP connects Claude to external services and data. Skills teach Claude how to use them well. MCP is like having access to the aisles; skills are like employee expertise." — Complementary relationship

## Related Terms
- MCP (Model Context Protocol)
- Agent Framework
- Tool Use / Function Calling
- CLAUDE.md / AGENTS.md
- Context Engineering

## Relevance to Generative AI Engineer Role
Skills are how you encode organizational procedures into AI systems. You'll design skill libraries for common patterns, version them alongside code, and teach agents how to solve domain-specific problems. Skills multiply agent capability without external tool overhead.

Sources:
- [Claude Help: What are Skills](https://support.claude.com/en/articles/12512176-what-are-skills)
- [Claude: Extending Capabilities with Skills and MCP](https://claude.com/blog/extending-claude-capabilities-with-skills-mcp-servers)
- [Simon Willison: Claude Skills](https://simonwillison.net/2025/Oct/16/claude-skills/)
