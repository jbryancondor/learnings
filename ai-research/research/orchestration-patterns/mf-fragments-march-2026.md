---
source: https://martinfowler.com/fragments/2026-03-16.html
date_accessed: 2026-04-04
published: 2026-03-16
author: Martin Fowler (curating contributions from Annie Vella, Bassim Eledath, Chad Fowler, Ankit Jain, Steve Yegge)
company: Thoughtworks
level_mapping: [6, 7, 8]
tags: [orchestration, supervisory-engineering, middle-loop, regenerative-architecture, evaluation-over-review, maturity-model, multi-agent]
agent: agent-4
---

## Summary
A Martin Fowler Fragments post from March 16, 2026, synthesizing insights from multiple practitioners about the emerging shape of software engineering with AI agents. Four distinct conceptual contributions are made: Supervisory Engineering (Annie Vella), Regenerative Architecture (Chad Fowler), Evaluation over Review (Ankit Jain), and a maturity model analysis (Bassim Eledath and Steve Yegge).

## Key Concepts

**Supervisory Engineering / Middle Loop (Annie Vella)**
Vella introduces a "middle loop" between:
- Inner loop: individual code writing, compilation, testing
- Outer loop: deployment, monitoring, production feedback
- **Middle loop**: directing AI agents, evaluating their output, correcting when wrong

**Supervisory engineering work** = the cognitive labor required to direct AI, evaluate its output, and correct it. This is verification-oriented, not creation-oriented. The practitioner's job shifts from producing to judging.

**Maturity Model Alignment (Bassim Eledath)**
Eledath's 8-level model (matching the team sprint framework):
- Level 1–2: Tab completion, single-turn assistance
- Level 3–4: Authoring full files/functions
- Level 5–6: Harness engineering, feedback loops
- Level 7–8: Background agents, autonomous teams
Key insight: "The difference is that one team has closed the gap between capability and practice." Technology capability outpaces organizational adoption.

**Steve Yegge Parallel Framework**
A parallel 8-level progression from near-zero AI usage to custom orchestrator building. Validates Eledath's framework from a different angle — both converge on orchestration as the frontier.

**Regenerative Architecture (Chad Fowler)**
Fowler argues the constraint has shifted: "The real constraint has shifted. The problem is no longer producing code. The problem is replacing it safely."

Components in a regenerative architecture must have:
1. Clear data ownership boundaries
2. Independent evaluation surfaces (each component testable in isolation)
3. Natural component sizing (right-sized for regeneration)
4. Minimal communication patterns (loose coupling enables safe replacement)

Implication: architecture designed for agent-driven regeneration, not just initial creation.

**Evaluation over Review (Ankit Jain)**
Traditional code review cannot scale to AI output velocity. Jain proposes replacing it with layered evaluation filters:
1. Deterministic guardrails (linting, type checking, security scanning)
2. Acceptance criteria definition (machine-readable specs)
3. Adversarial verification (agents trying to break other agents' output)

Fowler expresses caution — values precise code representation over natural language specifications for maintaining clarity and intent.

## Quotes / Evidence

> Chad Fowler: "The real constraint has shifted. The problem is no longer producing code. The problem is replacing it safely."

> Annie Vella on supervisory engineering: "the effort required to direct AI, evaluate its output, and correct it when it's wrong."

> Bassim Eledath: "the difference is that one team has closed the gap between capability and practice."

## Related Terms
- Supervisory Engineering
- Middle Loop (inner / middle / outer)
- Regenerative Architecture
- Evaluation over Review
- Harness Engineering
- Adversarial Verification
- Maturity Model (8-Level)

## Relevance to Generative AI Engineer Role
This fragment crystallizes the new job description for a senior AI-enabled engineer: supervisory engineering in the middle loop. The GenAI engineer does not write code at the object level — they direct, evaluate, and correct agent systems. Regenerative Architecture provides the architectural philosophy: design components for safe replacement, not just safe creation. Evaluation over Review provides the tooling philosophy: encode quality as machine-checkable criteria.
