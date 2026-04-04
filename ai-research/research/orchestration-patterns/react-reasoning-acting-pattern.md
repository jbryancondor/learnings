---
source: https://arxiv.org/abs/2210.03629
date_accessed: 2026-04-04
published: 2022-10
author: Shunyu Yao, Jeffrey Zhao et al.
company: Google Research / Princeton University
level_mapping: [7, 8]
tags: [react, reasoning, acting, agent-pattern, chain-of-thought, tool-use, foundational, iclr-2023]
agent: agent-4
---

## Summary
**ReAct (Reasoning + Acting)** is the foundational agent pattern introduced at ICLR 2023 by Yao, Zhao et al. from Google Research and Princeton. ReAct interleaves reasoning traces (thinking about what to do) with actions (actually doing things, like calling tools) in a single unified loop. It is the precursor pattern to Plan-and-Execute and the basis for most production agent implementations.

## Key Concepts

**Core Concept**
ReAct enables LLMs to generate both:
1. **Reasoning traces**: Verbal thinking — "I need to find the population of France, so I'll search Wikipedia"
2. **Actions**: Concrete steps — `search("France population 2024")`

These are interleaved: reason → act → observe result → reason again → act again → ...

**The ReAct Loop**

```
Thought: I need to find X
Action: search("X")
Observation: [search results]
Thought: The results show Y, so I should now check Z
Action: lookup("Z")
Observation: [lookup result]
Thought: I have enough information to answer
Action: finish("Answer: ...")
```

**Why Interleaving Matters**
- **Reasoning without acting**: Chain-of-Thought can reason but cannot gather new information — it's limited to training knowledge
- **Acting without reasoning**: Pure tool-calling agents act but cannot adjust plans based on unexpected results
- **ReAct**: Reasoning allows the agent to interpret observations and update plans; actions provide fresh external information

**Evaluation (from the paper)**
ReAct was evaluated on four benchmarks:
1. HotPotQA (question answering)
2. Fever (fact verification)
3. ALFWorld (text-based game)
4. WebShop (web page navigation)

ReAct outperformed pure Chain-of-Thought (no actions) and pure action-only agents on all benchmarks.

**Synergy Between Reasoning and Acting**
> "Reasoning traces help the model induce, track, and update action plans as well as handle exceptions, while actions allow it to interface with external sources, such as knowledge bases or environments, to gather additional information."

The key insight: reasoning and acting are mutually beneficial, not alternatives. Reasoning makes actions more targeted; observations from actions make reasoning more accurate.

**ReAct vs. Plan-and-Execute**

| Dimension | ReAct | Plan-and-Execute |
|-----------|-------|-----------------|
| Planning | Emergent / per-step | Upfront / explicit |
| Adaptability | Higher (reacts to each observation) | Lower (plan may not update) |
| Predictability | Lower (emergent path) | Higher (visible plan) |
| Token cost | Higher (full context per step) | Lower (executor sees less context) |
| Human oversight | Harder (emergent behavior) | Easier (inspect plan before execute) |
| Best for | Exploratory, unpredictable tasks | Structured, predictable tasks |

**Production Usage**
ReAct is the underlying pattern for:
- LangChain agent executor
- OpenAI Assistants API tool use
- Claude's tool use / extended thinking
- Most "agent" implementations in production today

**Chain-of-Thought as Prerequisite**
ReAct builds on Chain-of-Thought prompting (Wei et al. 2022) — the practice of asking LLMs to show their reasoning. ReAct extends CoT by making the reasoning externally actionable.

## Quotes / Evidence

From the paper:
> "ReAct explores the use of LLMs to generate both reasoning traces and task-specific actions in an interleaved manner, allowing for greater synergy between the two."

> "Reasoning traces help the model induce, track, and update action plans as well as handle exceptions, while actions allow it to interface with external sources."

From Google Research blog: "Synergizing reasoning and acting in language models"

## Related Terms
- Chain-of-Thought (CoT)
- Plan-and-Execute (successor pattern)
- Tool Use / Function Calling
- Orchestrator/Worker Separation
- Background Agent (Level 7)
- LangChain Agent Executor
- Thought/Action/Observation loop

## Relevance to Generative AI Engineer Role
ReAct is the foundational pattern that every GenAI engineer must understand before building agents. It explains *why* agents need both reasoning and tool access — and why neither alone is sufficient. When building agents: choose ReAct for exploratory tasks where the path to the answer isn't known upfront; choose Plan-and-Execute when the workflow is predictable and human oversight of the plan is valuable. Most production systems combine both: use ReAct within executor steps, Plan-and-Execute for the overall workflow.
