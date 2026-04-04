---
source: https://martinfowler.com/fragments/2026-03-16.html
date_accessed: 2026-04-04
published: 2026-03-16
author: Bassim Eledath (via Martin Fowler)
company: Thoughtworks
level_mapping: [6, 7]
tags: [implementer, reviewer, agent-separation, adversarial-verification, evaluation, multi-agent, quality-gates]
agent: agent-4
---

## Summary
**Implementer vs. Reviewer Agent Separation** is a pattern proposed by Bassim Eledath that applies separation of concerns at the agent level for code quality assurance. Rather than having a single agent generate and self-evaluate code, two distinct agents with different roles — an Implementer and a Reviewer — are used in sequence. The Reviewer agent is given the specification and the Implementer's output, and tasked with finding problems rather than generating solutions.

## Key Concepts

**The Core Pattern**

```
Specification
    ↓
[IMPLEMENTER AGENT]
    ↓
Generated Code / Artifact
    ↓
[REVIEWER AGENT] ← also receives: Specification, Quality Criteria
    ↓
Critique / Issues / Approval
    ↓
Human Decision (escalate / accept / reject)
```

**Why Separate Agents for Implementation and Review?**
A single agent that both implements and reviews its own work has a systematic blind spot: it will evaluate its own output through the lens of the decisions it already made. It tends to confirm its own choices rather than challenge them. A separate agent:
- Has no prior commitment to the implementation
- Can be given an adversarial persona ("find all problems with this code")
- Can be given different context (spec-focused, not implementation-focused)
- Can use a different model (e.g., larger model for review, smaller for implementation)

**Connection to Eledath's 8-Level Model**
Eledath's maturity model identifies implementer/reviewer separation as a Level 6–7 practice — the point where organizations move from single-agent to multi-agent quality workflows. At lower levels, a human acts as the reviewer. At Level 6–7, the reviewer is automated but LLM-powered. At Level 8, the reviewer is part of a continuous autonomous feedback loop.

**Adversarial Verification vs. Implementer/Reviewer**
These are related but distinct:
- **Adversarial Verification**: Broad term for any agent-vs-agent quality check
- **Implementer/Reviewer Separation**: Specific architectural pattern with defined roles, interfaces, and handoffs

The Implementer/Reviewer pattern is an instance of Adversarial Verification applied to code generation workflows.

**Prompt Design for the Reviewer Agent**
The Reviewer agent's prompt should:
1. Include the original specification in full
2. Include the quality criteria (style, security, idioms, architecture)
3. Explicitly instruct it to find problems, not to restate what's correct
4. Ask for structured output (issue category, severity, location, explanation)

**Feedback Loop Integration**
Reviewer outputs can be fed back to the Implementer for revision in a loop:
```
Implementer → Reviewer → Issues → Implementer (revision) → Reviewer → ...
```
Loop terminates when: (a) Reviewer finds no issues, (b) maximum iterations reached, or (c) Human-in-the-Loop checkpoint triggered.

## Quotes / Evidence

From MF Fragments March 2026: Bassim Eledath presents the 8-level maturity model arguing that "the difference is that one team has closed the gap between capability and practice" — implementer/reviewer separation is a Level 6 capability that most teams have not yet adopted.

Connection to Ankit Jain's Evaluation over Review: Layer 3 (Adversarial Verification) is the framework; Implementer/Reviewer Separation is the specific implementation pattern.

## Related Terms
- Adversarial Verification
- LLM-as-Judge
- Evaluation over Review (Ankit Jain)
- Harness Engineering
- Quality Gates
- Multi-Agent Pattern
- Background Agent (Level 7)

## Relevance to Generative AI Engineer Role
Implementing Implementer/Reviewer separation is a concrete step from Level 5 to Level 6 in the maturity model. A GenAI engineer should be able to: design the Reviewer agent's prompt, define the quality criteria interface, build the feedback loop between agents, and determine when to escalate to human review. This pattern reduces the cost of human review while maintaining quality standards at agent velocity.
