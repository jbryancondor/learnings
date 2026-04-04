---
source: https://martinfowler.com/articles/exploring-gen-ai/humans-and-agents.html
date_accessed: 2026-04-04
published: 2026-03-04
author: Kief Morris
company: Thoughtworks
level_mapping: [4, 6, 7]
tags: [taxonomy, human-agent-spectrum, harness-engineering, agentic-flywheel, supervisory-engineering]
agent: agent-1
---

## Summary

Kief Morris (Thoughtworks) defines a **three-position spectrum** for human-agent collaboration: Outside the Loop, In the Loop, and On the Loop. The core argument is that "On the Loop" — where humans design the harness (specs, quality checks, workflow guidance) rather than directly reviewing outputs — is the optimal position. Introduces the **agentic flywheel** concept where agents improve their own harness.

Also references Annie Vella's "supervisory engineering" concept from Martin Fowler's March 2026 Fragments.

## Key Concepts

### The Three Positions

1. **Humans Outside the Loop** ("Vibe Coding") — The "why loop" (ideas → working software) is managed by humans; the "how loop" (code generation) runs autonomously. Risk: no quality control on internals.

2. **Humans In the Loop** — Humans closely supervise both loops, manually inspecting and reviewing agent-generated code. Creates bottlenecks despite catching errors early.

3. **Humans On the Loop** (Recommended) — Humans design and manage the **harness** — specifications, quality checks, workflow guidance — that directs agent behavior. Humans govern outcomes, not outputs.

### The Double-Loop Model

- **Why Loop**: Ideas → working software (human-driven, outcome-focused)
- **How Loop**: Specifications → code → tests → infrastructure (agent-optimized with human governance)

### The Harness

A collection of specifications, quality checks, and workflow guidance that controls how AI agents operate. Maintaining the harness = **Harness Engineering** (maps directly to Eledath's Level 6).

### The Agentic Flywheel

The next evolutionary stage: agents receive rich performance signals (tests, pipeline metrics, production data, user behavior) and recommend improvements to their own harness. Low-risk changes can be auto-approved. This maps to the transition from Level 6 → Level 7 in Eledath's framework.

### Supervisory Engineering (via Annie Vella)

Research on 158 engineers identified a shift from creation to verification-oriented tasks. The "middle loop" sits between inner loops (code/test/debug) and outer loops (CI/CD/deploy).

## Quotes / Evidence

- "We care about external quality, not internal quality for its own sake"
- "Agents produce better code when they can gauge the quality of the code they produce themselves"
- "The problem is no longer producing code. The problem is replacing it safely." (Chad Fowler, via Fragments)
- "Humans already couldn't keep up with code review when humans wrote code" (Jain, via Fragments)

## Related Terms

- Harness engineering, agentic flywheel
- Double-loop model, supervisory engineering
- Shift-left principle (for agents)
- Ralph looping (continuous agent execution)
- Spec Driven Development (SDD)

## Relevance to Generative AI Engineer Role

This framework redefines the Gen AI engineer's core job: **build and maintain the harness**, not review code. The shift from "In the Loop" to "On the Loop" is perhaps the single most important mindset change for someone transitioning into this role. The agentic flywheel concept points to the future — engineers who can build self-improving harnesses create compounding value.
