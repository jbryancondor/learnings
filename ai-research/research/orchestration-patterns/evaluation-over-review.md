---
source: https://martinfowler.com/fragments/2026-03-16.html
date_accessed: 2026-04-04
published: 2026-03-16
author: Ankit Jain (via Martin Fowler)
company: Thoughtworks
level_mapping: [6, 7]
tags: [evaluation, code-review, llm-as-judge, harness-engineering, quality-gates, adversarial-verification]
agent: agent-4
---

## Summary
Ankit Jain's **Evaluation over Review** concept proposes replacing traditional human code review with a layered system of automated evaluation filters. The core argument: agents generate code too fast for human review to be a viable quality gate. Instead, quality must be encoded as machine-checkable criteria organized in layers of increasing sophistication.

## Key Concepts

**The Review Bottleneck**
Traditional code review assumes:
- A human can read and evaluate every change
- Review time scales linearly with team size
- Reviewers have sufficient context for each change

With AI agents, all three assumptions break:
- Agents produce code at 10–100x human velocity
- Review time cannot scale to match
- Each agent may work across many components simultaneously

Result: traditional review becomes a bottleneck, not a quality gate.

**The Evaluation Stack (Jain's Three Layers)**

| Layer | Type | Examples |
|-------|------|---------|
| **1. Deterministic Guardrails** | Static, automated | Linting, type checking, security scanning, dependency validation |
| **2. Acceptance Criteria** | Machine-readable specs | Behavior tests, contract tests, property-based testing |
| **3. Adversarial Verification** | Agent-vs-agent | One agent generates, another attempts to break or critique the output |

Layer 1 is cheapest and fastest — run on every commit. Layer 2 encodes intent as executable specs. Layer 3 scales intelligent critique without human reviewers.

**Adversarial Verification**
The most novel layer: deploying a separate "critic" or "reviewer" agent to evaluate the output of a "implementer" agent. This is the agent-level expression of the implementer/reviewer separation (cf. Bassim Eledath). The critic agent:
- Looks for edge cases the implementer missed
- Checks alignment with specifications
- Identifies security or quality issues
- Reports findings for human escalation or automated rejection

**Fowler's Caution**
Martin Fowler expresses concern about natural language specifications replacing precise code. He values exact code representation for maintaining clarity and intent — overly abstract specs may allow agents to produce "technically compliant but wrong" implementations.

This tension (human-readable specs vs. machine-precise specs) is an open design question in harness engineering.

**Connection to LLM-as-Judge**
Adversarial Verification in Layer 3 is a form of LLM-as-Judge: an LLM evaluates the output of another LLM. The distinction from generic LLM-as-Judge: the critic agent has full access to the original specification, making its evaluation grounded rather than just preference-based.

## Quotes / Evidence

> Ankit Jain proposes "replacing traditional code review with layered evaluation filters including deterministic guardrails, acceptance criteria definition, and adversarial verification"

> Martin Fowler: caution about "natural language specifications for maintaining clarity and intent"

## Related Terms
- LLM-as-Judge
- Adversarial Verification
- Implementer/Reviewer Agent Separation
- Harness Engineering
- Acceptance Criteria
- Deterministic Guardrails
- Human-On-the-Loop

## Relevance to Generative AI Engineer Role
Building an evaluation stack is a core GenAI engineering competency at Level 6. The practitioner must: (1) identify which quality properties can be captured as deterministic rules, (2) encode behavioral intent as machine-executable acceptance criteria, and (3) deploy adversarial agent patterns for intelligent critique. This is the infrastructure that makes "humans on the loop" viable at agent velocity.
