---
source: https://arxiv.org/html/2505.10468v1
date_accessed: 2026-04-04
published: 2025-05
author: Sapkota, Roumeliotis, and Karkee
company: Academic
level_mapping: [7, 8]
tags: [taxonomy, ai-agents, agentic-ai, multi-agent, orchestration, classification, react, chain-of-thought, memory]
agent: agent-4
---

## Summary
This arXiv paper by Sapkota, Roumeliotis, and Karkee provides a rigorous conceptual taxonomy distinguishing between **AI Agents** (single-entity, task-specific, tool-augmented systems) and **Agentic AI** (multi-agent orchestrated ecosystems). The taxonomy clarifies why these are architecturally distinct categories that require different design principles — and why conflating them leads to misapplied patterns.

## Key Concepts

**Core Definitions**

**AI Agents**: "Autonomous software entities engineered for goal-directed task execution within bounded digital environments." Optimized for narrow, specialized operations with minimal human intervention post-deployment.

**Agentic AI**: "Systems of multiple AI agents collaborating to achieve complex goals" through coordinated workflows, distributed intelligence, and dynamic task decomposition. The key addition over AI Agents is **coordination** between entities.

**The Three-Tier Hierarchy**

```
Generative AI (baseline)
    ↓ add tools + autonomy
AI Agents (single entity)
    ↓ add coordination + orchestration
Agentic AI (multi-agent ecosystem)
```

| Tier | Structure | Planning | Communication | Autonomy |
|------|-----------|----------|---------------|---------|
| Generative AI | Single model | Prompt-reactive | None | None |
| AI Agents | Single model + tools | Single-step | Isolated | Medium (task-bounded) |
| Agentic AI | Multiple agents | Multi-step goal decomposition | Inter-agent | High (workflow management) |

**Three Core Traits of AI Agents**
1. **Autonomy**: Minimal human oversight after initialization
2. **Task-Specificity**: Optimization for narrowly scoped domains
3. **Reactivity with Adaptation**: Responsive to environmental changes through feedback loops

**Agentic AI Architectural Innovations (absent in single AI Agents)**
- **Ensemble Specialization**: Modular agents with distinct functional roles
- **Advanced Reasoning**: Recursive planning via ReAct and Chain-of-Thought frameworks
- **Persistent Memory**: Episodic, semantic, and vector-based knowledge retention across sessions
- **Meta-Orchestration**: Coordinator agents managing subordinate agent lifecycles

**Why This Taxonomy Matters (Practical Implication)**
The authors warn against "misapplication of design principles — assuming inter-agent collaboration in systems architected for single-agent execution." Specifically:
- A single AI Agent optimized for task-specificity does not benefit from adding coordination overhead
- An Agentic AI system cannot be built by simply connecting multiple single-task agents without orchestration infrastructure
- The design principles are fundamentally different: isolation vs. coordination, task-bounded vs. workflow management

**Memory Architecture in Agentic AI**
Three types of persistent memory distinguish Agentic AI from single agents:
1. **Episodic memory**: Records of past interactions and their outcomes
2. **Semantic memory**: Factual knowledge accumulated over time
3. **Vector-based knowledge retention**: Embedding-indexed memory for similarity retrieval

**ReAct and Chain-of-Thought in Multi-Agent Context**
The paper positions ReAct and CoT as reasoning frameworks that scale differently:
- In single agents: used to improve single-step reasoning quality
- In Agentic AI: used by each agent AND by the meta-orchestrator for multi-step planning

## Quotes / Evidence

> "AI Agents are typically designed as single-entity systems that perform goal-directed tasks by invoking external tools...In contrast, Agentic AI systems are composed of multiple, specialized agents that coordinate, communicate, and dynamically allocate sub-tasks."

> The taxonomy prevents "misapplication of design principles—assuming inter-agent collaboration in systems architected for single-agent execution."

## Related Terms
- Generative AI
- AI Agent
- Agentic AI
- Ensemble Specialization
- Meta-Orchestration
- Episodic / Semantic / Vector Memory
- ReAct (Reasoning + Acting)
- Chain-of-Thought
- Autonomous Agent Teams (Level 8)

## Relevance to Generative AI Engineer Role
This taxonomy provides the conceptual foundation for choosing between single-agent and multi-agent architectures. A GenAI engineer should use it to answer: "Does this problem require coordination between specialized agents, or can one well-equipped agent handle it?" The answer determines whether to build at Level 5–6 (AI Agent) or Level 7–8 (Agentic AI) — with significant differences in complexity, cost, and orchestration infrastructure required.
