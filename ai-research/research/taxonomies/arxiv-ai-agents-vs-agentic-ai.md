---
source: https://arxiv.org/html/2505.10468v1
date_accessed: 2026-04-04
published: 2025-05-15
author: Ranjan Sapkota, Konstantinos I. Roumeliotis, Manoj Karkee
company: Academic (arXiv)
level_mapping: [1, 2, 5, 7, 8]
tags: [taxonomy, academic, ai-agents, agentic-ai, conceptual-taxonomy, architecture]
agent: agent-1
---

## Summary

Academic paper establishing a **four-tier conceptual taxonomy**: Generative AI → AI Agents → Agentic AI → Generative Agents. The critical contribution is a rigorous distinction between "AI Agents" (single-entity, tool-augmented, task-specific) and "Agentic AI" (multi-agent, orchestrated, persistent memory). This is the most technically grounded taxonomy in the research set.

## Key Concepts

### Four-Tier Taxonomy

| Tier | Definition | Key Trait |
|------|-----------|-----------|
| **Generative AI** | Reactive content generation driven by prompts | Stateless, no autonomy |
| **AI Agents** | Single-entity, tool-augmented systems for task-specific automation | Bounded autonomy, task-specific |
| **Agentic AI** | Multi-agent coordinated systems for complex workflow orchestration | Inter-agent communication, persistent memory |
| **Generative Agents** | Modular agents performing subtask generation within larger workflows | Embedded in larger systems |

### AI Agents vs. Agentic AI — Key Distinctions

| Dimension | AI Agents | Agentic AI |
|-----------|-----------|-----------|
| Architecture | Single LLM + tools | Multiple specialized agents |
| Autonomy | High (within task scope) | Higher (multi-step goal management) |
| Collaboration | Independent operation | Inter-agent communication |
| Task Complexity | Narrowly scoped | Complex, multi-faceted |
| Memory | Optional/limited | Persistent, shared episodic/semantic |
| Coordination | None required | Hierarchical or decentralized |

### AI Agent Core Components (4-Module Model)

1. **Perception Module** — Ingests user prompts and external signals
2. **Knowledge Representation & Reasoning** — Symbolic/statistical logic, thought chains
3. **Action Selection & Execution** — Translates decisions into external actions
4. **Basic Learning & Adaptation** — Heuristic adjustment and history retention

### Agentic AI Enhancements

1. **Ensemble of Specialized Agents** — Multiple role-bound agents communicating via channels
2. **Advanced Reasoning & Planning** — ReAct, Chain-of-Thought, Tree of Thoughts
3. **Persistent Memory Architectures** — Episodic, semantic, vector-based (RAG)
4. **Orchestration/Meta-Agents** — Coordinate subordinate agents, manage dependencies

### Historical Evolution

- Pre-2022: Rule-based agents with symbolic reasoning (expert systems, BDI)
- Nov 2022 (ChatGPT): Shift to learning-driven, adaptive architectures
- 2023: Rise of tool-augmented AI Agents (AutoGPT, BabyAGI)
- Late 2023+: Emergence of Agentic AI ecosystems (CrewAI, ChatDev, MetaGPT)

## Quotes / Evidence

- "Without this clarity, practitioners risk both under-engineering complex scenarios that require agentic coordination and over-engineering simple applications"
- "Tool-augmented agents overcome limitations inherent to generative-only systems such as hallucination, static knowledge cutoffs, and restricted interaction scopes"
- "Agentic AI systems represent an emergent class of intelligent architectures in which multiple specialized agents collaborate"

## Related Terms

- ReAct framework, Chain-of-Thought, Tree of Thoughts
- RAG (Retrieval-Augmented Generation)
- Episodic/semantic/vector memory
- AutoGen, ChatDev, MetaGPT, CrewAI, LangChain
- BDI architecture, meta-agents, orchestration layers

## Relevance to Generative AI Engineer Role

This paper provides the **theoretical foundation** for the practical frameworks. The AI Agent vs. Agentic AI distinction maps cleanly onto Eledath's levels: Levels 1–5 are largely "AI Agent" territory (single entities with tools), while Levels 6–8 enter "Agentic AI" territory (multi-agent orchestration with persistent memory). Understanding this taxonomy prevents the common mistake of applying multi-agent solutions to problems solvable by a single well-tooled agent.
