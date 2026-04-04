---
source: https://martinfowler.com/articles/exploring-gen-ai/humans-and-agents.html
date_accessed: 2026-04-04
published: 2026-03
author: Martin Fowler
company: Thoughtworks
level_mapping: [6, 7, 8]
tags: [orchestration, harness-engineering, human-in-the-loop, human-on-the-loop, agentic-flywheel, background-agents, loops]
agent: agent-4
---

## Summary
MF #25 in the Exploring Gen AI series. Fowler introduces a framework for thinking about where humans sit relative to AI agents in software engineering workflows. He proposes three models — humans outside, in, and on the loop — and argues that "humans on the loop" with Harness Engineering is the optimal path forward. The article introduces the concept of the Agentic Flywheel as an advanced emergent pattern.

## Key Concepts

**The Why Loop vs. How Loop**
- **Why Loop**: Turning ideas into working software — human-centered, strategic. Covers product decisions, architecture, goals.
- **How Loop**: Producing intermediate artifacts (code, tests, infrastructure). Agents excel here.
- The How Loop contains nested sub-loops that break work into progressively smaller tasks — matching the layered orchestration model (Levels 5–8).

**Three Human-Agent Collaboration Models**

| Model | Description | Risk |
|-------|-------------|------|
| Humans Outside the Loop ("Vibe Coding") | Humans only specify, agents implement everything | Agent misunderstanding compounds; poor code structure degrades agent performance |
| Humans In the Loop | Developers manually inspect all agent output | Bottleneck: "Agents can generate code faster than humans can manually inspect it" |
| Humans On the Loop (Recommended) | Humans build/maintain the harness — specs, quality checks, workflow guidance | Requires harness engineering discipline |

**Harness Engineering (Level 6)**
The emerging practice of constructing and maintaining the agent harness — the system of specifications, quality checks, and workflow guidance that controls agent behavior. Positions humans as engineers of the control system, not manual reviewers of output.

**The Agentic Flywheel (Level 7–8 emergent)**
An advanced pattern where agents analyze their own performance using test results and operational data, then recommend harness improvements. Humans approve recommendations interactively or enable automated approval for vetted suggestion types. This creates a self-improving loop:
1. Agents execute tasks
2. Tests and metrics capture outcomes
3. Agents analyze failure patterns
4. Agents propose harness improvements
5. Human approves → harness updates
6. Return to step 1 with improved harness

**Why Humans Outside the Loop Fails**
"Vibe coding" (pure specification + agent execution) breaks down because: (1) agents interpret specifications based on their training, not domain context; (2) poor code structure degrades agent performance in subsequent iterations; (3) no mechanism exists to catch quality degradation early.

## Quotes / Evidence

> "Agents can generate code faster than humans can manually inspect it."

> Human involvement focuses on **directing improvement** rather than executing implementation tasks.

The article positions harness engineering as the primary skill for the emerging "Supervisory Engineering" role (cf. Annie Vella).

## Related Terms
- Why Loop / How Loop
- Human Outside/In/On the Loop
- Harness Engineering
- Agentic Flywheel
- Supervisory Engineering
- Vibe Coding
- Plan-and-Execute
- LLM-as-Judge

## Relevance to Generative AI Engineer Role
The "humans on the loop" model is the target operating model for a GenAI engineer. Rather than reviewing code, the role is to design the harness: write specs that are machine-evaluable, build quality gates, and architect the feedback loops that make agent systems self-improving. The Agentic Flywheel represents the most advanced expression of this — a system that improves without requiring per-task human intervention.
