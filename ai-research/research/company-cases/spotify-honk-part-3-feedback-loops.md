---
source: https://engineering.atspotify.com/2025/12/feedback-loops-background-coding-agents-part-3
date_accessed: 2026-04-04
published: 2025-12-01
author: Spotify Engineering
company: Spotify
level_mapping: [6, 7]
tags: [spotify, honk, feedback-loops, level-6, level-7, verification, llm-judge, harness-engineering, ci-cd]
agent: agent-2
---

## Summary

Part 3 of Spotify's Honk series addresses the critical reliability problem: without feedback loops, "agents often produce code that simply doesn't work." The team built a layered verification system combining **deterministic verifiers** (formatters, linters, build/test runners) with an **LLM-based judge** layer. The judge vetoes approximately **25% of thousands of agent sessions**, and agents successfully course-correct **50% of the time** after a veto. This is Level 6 (Harness Engineering) enabling Level 7 (Background Agents) to operate at production quality.

## Key Concepts

### Three Failure Modes (Ranked by Severity)

1. **Agent fails to produce a PR** — minor; manual intervention needed
2. **PR fails CI/CD tests** — frustrating; forces fix-or-abandon decisions on half-broken code
3. **PR passes CI but is functionally incorrect** — most serious; erodes automation trust, risks production breaks

### The Verification Loop Framework

**Deterministic Verifiers:**
- Trigger automatically based on codebase contents (e.g., Maven verifier activates on `pom.xml` detection)
- Abstract away build system complexity and test output parsing
- Use regex to extract relevant error messages; return brief success confirmations
- Run before PR submission via Claude Code's stop hook

**Core design principle:**
> "The agent doesn't know what the verification does and how, it just knows that it can (and in certain cases must) call it to verify its changes."

**LLM-Based Judge:**
- Separate LLM evaluates proposed changes against original prompt
- Vetoes ~**25% of thousands of agent sessions**
- Most common trigger: agent exceeding prompt scope
- After veto, agents self-correct **~50% of the time**
- Provides "outer loop" validation beyond deterministic checks

### Agent Design Constraints (Intentional)

| Constraint | Rationale |
|---|---|
| Single responsibility: execute code changes per prompt | Predictability |
| No direct code pushing | Safety |
| No Slack interaction | Scope containment |
| No prompt authoring | Separation of concerns |
| Highly sandboxed container, minimal permissions | Security |

### Future Roadmap

1. Multi-platform verifier support (currently Linux x86 only; need macOS for iOS, ARM64 for backends)
2. CI/CD pipeline integration for true "outer loop" validation
3. Structured evaluations for systematic improvements

## Quotes / Evidence

> "Without feedback loops, agents often produce code that simply doesn't work."

> "Judge vetoes approximately 25% of thousands of agent sessions"

> "Agents successfully course-correct 50% of the time after veto"

> "The agent doesn't know what the verification does and how, it just knows that it can (and in certain cases must) call it to verify its changes."

## Related Terms

- Harness Engineering (Level 6)
- Background Coding Agents (Level 7)
- LLM-as-judge
- Deterministic verifiers
- Verification loop
- Stop hooks (Claude Code)
- Sandboxed execution
- Feedback loop architecture

## Relevance to Generative AI Engineer Role

The feedback loop architecture is the key enabler that makes background agents safe to run at scale. Key takeaways:

1. **Layered verification is the pattern** — deterministic checks (fast, cheap, reliable) + LLM judge (semantic correctness). Both layers needed; neither alone is sufficient.
2. **LLM-as-judge at 25% veto rate** — that's a real signal: a quarter of agent outputs need intervention. Designing evaluation into the system from day one is not optional.
3. **Agents + stop hooks** — Claude Code's stop hook mechanism is used to ensure all verifiers run before any PR is created. This is harness engineering in practice.
4. **Failure taxonomy matters** — classifying failures by severity (type 1/2/3) lets you prioritize what to fix first. Type 3 (silent failures) are the existential risk to trust.
5. **Scope containment through constraints** — limiting what agents can do (no push, no Slack, sandboxed) is a design decision, not a limitation. Fewer permissions = fewer risks.
