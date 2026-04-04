---
source: https://martinfowler.com/fragments/2026-03-16.html
date_accessed: 2026-04-04
published: 2026-03-16
author: Annie Vella (via Martin Fowler)
company: Thoughtworks
level_mapping: [6, 7]
tags: [supervisory-engineering, middle-loop, human-on-the-loop, verification, orchestration, harness-engineering]
agent: agent-4
---

## Summary
Annie Vella's concept of **Supervisory Engineering** and the **Middle Loop** reframes the software engineer's cognitive work in an AI-augmented environment. Rather than producing artifacts, the primary activity becomes directing, evaluating, and correcting AI agent output. The Middle Loop sits between the inner loop (write/test/compile) and the outer loop (deploy/monitor), and represents the new locus of human cognitive effort.

## Key Concepts

**The Three Loops**

| Loop | Scope | Activities |
|------|-------|-----------|
| Inner Loop | Per-change cycle | Write code, run tests, fix compilation errors |
| **Middle Loop** | Per-feature/sprint cycle | **Direct AI agents, evaluate output, correct failures** |
| Outer Loop | Deployment/production cycle | Deploy, monitor, respond to incidents |

**Supervisory Engineering Work**
Defined as: "the effort required to direct AI, evaluate its output, and correct it when it's wrong."

This work is verification-oriented, not creation-oriented. It requires:
- Knowing what "good" looks like (deep domain + technical expertise)
- Ability to evaluate agent output at scale (cannot read every line)
- Capacity to diagnose failure modes and write corrective specifications
- Skill to encode quality criteria as machine-checkable rules

**Why This Matters — The Velocity Paradox**
Agents generate code faster than humans can review it manually. If engineers remain in the inner loop (reading every diff), agent velocity is wasted. The Middle Loop solution: humans review *categories* of output, encode evaluation criteria, and let machines enforce them at volume.

**The Shift in Expertise**
What made an expert before agents:
- Ability to write high-quality code quickly
- Deep knowledge of language idioms and patterns

What makes an expert with agents:
- Ability to evaluate agent output for quality, correctness, and safety
- Ability to write precise specifications that constrain agent behavior
- Ability to design evaluation harnesses that catch failure modes at scale

**Connection to Harness Engineering**
Supervisory Engineering is the human role; Harness Engineering is the technical practice. Together they define the "humans on the loop" model:
- Supervisory Engineering = the cognitive work
- Harness Engineering = the tooling/infrastructure supporting that work

## Quotes / Evidence

> Annie Vella: "the effort required to direct AI, evaluate its output, and correct it when it's wrong"

From MF #25 (Humans and Agents):
> "Agents can generate code faster than humans can manually inspect it."

## Related Terms
- Middle Loop
- Inner Loop / Outer Loop
- Harness Engineering
- Human-On-the-Loop
- Evaluation over Review (Ankit Jain)
- LLM-as-Judge
- Background Agent (Level 7)

## Relevance to Generative AI Engineer Role
Supervisory Engineering describes the primary job function of a GenAI engineer operating at Levels 6–7. The skill set required is different from traditional software engineering: less emphasis on writing, more emphasis on evaluating, specifying, and correcting. This means building judgment about what makes agent output good or bad — and encoding that judgment into the harness rather than applying it manually per-review.
