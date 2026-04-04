---
source: https://martinfowler.com/articles/exploring-gen-ai/harness-engineering-memo.html
date_accessed: 2026-04-04
published: 2025-01-01
author: Martin Fowler / OpenAI (case study)
company: Thoughtworks / OpenAI
level_mapping: [6]
tags: [harness-engineering, ai-agents, observability, constraints, hooks, claude-code, guardrails, production]
agent: agent-3b
---

## Summary
Harness engineering is the discipline of designing systems, constraints, and feedback loops that wrap around AI agents to make them reliable in production. A "harness" is the complete infrastructure governing how an agent operates: the tools it can access, the guardrails that keep it safe, the feedback loops that enable self-correction, and the observability layer enabling human oversight. Coined/popularized by Martin Fowler's articles on GenAI engineering, harness engineering is emerging as a distinct software discipline at Level 6 of the Gen AI Engineer progression — above basic LLM usage but below full background agent architecture.

## Key Concepts

### Core Components of a Harness
1. **Context Engineering**: Continuously enhanced knowledge bases (documentation, architecture docs, coding standards) that give agents accurate working knowledge of the codebase
2. **Architectural Constraints**: Enforced via both LLM-based agents (reviewing for pattern violations) and deterministic linters/structural tests (e.g., ArchUnit)
3. **Entropy Management**: Periodic agents that detect documentation inconsistencies and architectural constraint violations before they accumulate
4. **Observability Layer**: Logging of agent actions, tool calls, and token usage — even simple file-based logging provides diagnostic data

### Key Principles
- **Constrain the solution space**: Rather than unlimited flexibility, harnesses bound what the agent can do via permissions, tool allowlists, and output validators
- **Reversibility first**: Design agent actions to be reversible (snapshots, dry-run modes, staged commits)
- **Signal from struggle**: "When the agent struggles, treat it as a signal" — identify missing tools, guardrails, or documentation rather than brute-forcing
- **Iterative feedback loops**: Harnesses improve through observed failures, not just initial design

### Claude Code as Harness Implementation
Claude Code provides a canonical harness architecture:
- **Permission model**: Read-only by default; explicit approval required for writes
- **Hooks system**: User-defined scripts executing at lifecycle events (pre-edit, post-edit, pre-commit, etc.) — analogous to git hooks but more flexible
  - Use cases: security scanning, linting, policy enforcement, logging, custom integrations
- **Automatic snapshots**: Every file edit is reversible through built-in snapshotting
- **Skills system**: Reusable slash commands that encode harness behavior (e.g., `/learnings-security` runs security checks)

### Hook Patterns (Claude Code)
```yaml
# Example hooks in .claude/settings.json
hooks:
  pre_tool_use:
    - type: command
      command: "scripts/security-check.sh"
  post_tool_use:
    - type: command
      command: "scripts/lint-changed.sh"
```

### Harness Anti-Patterns
- Retrofitting a harness onto a legacy codebase — often impractical due to existing entropy
- Relying solely on natural language instructions (no deterministic checks)
- Skipping observability ("we'll add logging later")
- Overly permissive tool access without audit logging

### Enterprise Harness Concerns
- **Audit trails**: Every agent action logged with actor, timestamp, diff
- **SSO-integrated auth**: Harness connects to identity providers for role-based agent permissions
- **Gateway behavior**: AI gateway (e.g., Kong AI Gateway for Claude Code) for rate limiting, policy enforcement, routing
- **Configuration portability**: Harness configs as code, version-controlled

## Quotes / Evidence
> "Harness engineering is the discipline of designing the systems, constraints, and feedback loops that wrap around AI agents to make them reliable in production." — NxCode guide, 2026

> "When the agent struggles, treat it as a signal to identify missing tools, guardrails, or documentation." — Martin Fowler, harness engineering memo

> "Harnesses may evolve into next-generation service templates for standardized application topologies." — Martin Fowler, exploring gen-ai series

> "Claude Code has the concept of hooks: user-defined commands or scripts that are automatically executed when certain events occur at various points of the agent's lifecycle." — harness engineering search results, 2025

## Related Terms
- Claude Code Hooks
- Observability / LLM Tracing
- LangSmith / Langfuse / Helicone (observability tools)
- Pre-commit hooks / Git hooks
- ArchUnit / Structural testing
- AI Gateway (Kong, Cloudflare)
- Skills (Claude Code slash commands)

## Relevance to Generative AI Engineer Role
Harness engineering is the defining Level 6 skill for a Gen AI Engineer. It's the difference between demo agents and production agents. Bryan's transition from software engineer includes existing skills in CI/CD and linting that directly translate to harness design. Key areas to develop: Claude Code hooks configuration, observability instrumentation (pick one: LangSmith/Langfuse), and entropy management (scheduled review agents). The hooks system in particular is a concrete, learnable API surface.
