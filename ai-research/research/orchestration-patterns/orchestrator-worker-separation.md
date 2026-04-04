---
source: https://openai.github.io/openai-agents-python/multi_agent/
date_accessed: 2026-04-04
published: 2025
author: OpenAI / Multi-agent community
company: OpenAI, LangChain, Anthropic
level_mapping: [7, 8]
tags: [orchestration, orchestrator, worker, multi-agent, separation-of-concerns, background-agents, dispatcher, pattern]
agent: agent-4
---

## Summary
The **Orchestrator/Worker Separation** is the foundational structural pattern for multi-agent systems at Levels 7–8. An Orchestrator agent coordinates overall workflow — breaking goals into subtasks, assigning them to specialized workers, collecting results, and deciding next steps. Worker agents are specialized, narrowly scoped, and stateless (or near-stateless). This separation mirrors the Planner/Executor split but generalizes to persistent multi-agent teams.

## Key Concepts

**The Pattern**

```
[ORCHESTRATOR]
    ├── Receives: High-level goal
    ├── Maintains: Workflow state, task list, agent inventory
    ├── Decides: Which worker to invoke next
    ├── Synthesizes: Worker results into coherent output
    └── Handles: Failure, re-routing, human escalation

[WORKER AGENTS]
    ├── Receive: Specific, scoped subtasks
    ├── Have: Specialized tools and context
    ├── Return: Results to orchestrator
    └── Are: Stateless across invocations (usually)
```

**Orchestrator Responsibilities**
1. Goal decomposition — breaking the user's objective into subtasks
2. Worker selection — choosing the right agent for each subtask
3. Context management — passing relevant context to each worker
4. Result synthesis — combining worker outputs into a coherent whole
5. Error handling — detecting worker failures and re-routing
6. Human escalation — surfacing decisions that require human input

**Worker Agent Characteristics**
- Narrowly scoped — optimized for one type of task
- Tool-equipped — has the specific tools needed for its domain
- Context-minimal — receives only what it needs (reduces hallucination risk)
- Replaceable — can be swapped for a better model/implementation without changing the orchestrator
- Often stateless — orchestrator manages state, worker just transforms input to output

**Dispatch Patterns**

| Pattern | Description | When to Use |
|---------|-------------|-------------|
| Sequential | Workers invoked one at a time in order | Dependent steps |
| Parallel | Multiple workers invoked simultaneously | Independent subtasks |
| Conditional | Worker selection depends on previous results | Branching logic |
| Iterative | Same worker invoked repeatedly until convergence | Refinement tasks |
| Fan-out/Fan-in | Multiple workers in parallel, results aggregated | Information gathering |

**Router Agent Pattern**
A specialized sub-pattern where a Router agent classifies incoming requests and routes them to the appropriate specialized worker — without itself performing any substantive work. See Spotify's RouterAgent for a production example: it analyzes user messages and determines what information is present before routing to specialist agents.

**Context Window Management**
Workers receive minimal, targeted context — not the full conversation history. The orchestrator is responsible for context compression and selective forwarding. This is critical for performance and accuracy at scale.

**Failure Modes**
- Orchestrator overload: Too much logic in the orchestrator makes it brittle
- Worker scope creep: Workers that try to do too much undermine the pattern
- Context starvation: Workers that receive too little context hallucinate
- Coordination overhead: Too many workers creates latency and error surface

## Quotes / Evidence

Spotify's production implementation (2026): Five specialized agents (Router, GoalResolver, AudienceResolver, Budget, MediaPlanner) coordinated by a long-running orchestration layer with parallel execution reducing latency to 3-5 seconds.

OpenAI Agents SDK: Treats orchestrator/worker separation as the primary multi-agent pattern, with handoffs (transferring control between agents) as the core coordination primitive.

## Related Terms
- Plan-and-Execute
- Dispatcher Pattern
- Router Agent
- Background Agent (Level 7)
- Autonomous Agent Teams (Level 8)
- LangGraph, AutoGen, CrewAI
- Handoff (OpenAI Agents SDK)
- A2A Protocol

## Relevance to Generative AI Engineer Role
Orchestrator/Worker separation is the fundamental design decision for any Level 7–8 system. A GenAI engineer must decide: what lives in the orchestrator vs. workers, how to scope workers, and how to manage state across the system. Poor orchestrator design is the most common failure mode in production multi-agent systems — orchestrators that try to do too much become the bottleneck and the primary point of failure.
