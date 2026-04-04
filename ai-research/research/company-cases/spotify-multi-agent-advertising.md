---
source: https://engineering.atspotify.com/2026/2/our-multi-agent-architecture-for-smarter-advertising
date_accessed: 2026-04-04
published: 2026-02-01
author: Spotify Engineering
company: Spotify
level_mapping: [8]
tags: [spotify, multi-agent, level-8, advertising, ads-ai, google-adk, vertex-ai, orchestration, parallel-agents]
agent: agent-2
---

## Summary

Spotify's Ads AI system is a **multi-agent architecture** (Level 8: Autonomous Agent Teams) built on Google's Agent Development Kit (ADK) and Vertex AI to unify media planning across all advertising buying surfaces: Direct, Self-Serve, and Programmatic. The system reduces campaign creation time from **15–30 minutes to 5–10 seconds** and compresses user inputs from **20+ form fields to 1–3 natural language messages** — a 99.7% reduction in time and a ~90% reduction in required inputs.

## Key Concepts

### The Problem

Spotify's advertising business has three distinct buying channels (Direct, Self-Serve, Programmatic), each with its own workflows and decision logic, creating duplicated complexity and inconsistent optimization despite a consolidated backend infrastructure.

### Agent Architecture

| Agent | Role |
|---|---|
| **RouterAgent** | Analyzes user input, determines available info, routes requests to appropriate resolvers |
| **GoalResolverAgent** | Maps advertiser intent to campaign objectives |
| **AudienceResolverAgent** | Extracts targeting criteria from natural language |
| **BudgetAgent** | Parses budget formats, converts to standard units |
| **ScheduleAgent** | Handles date parsing including relative references ("next month", "Q2") |
| **MediaPlannerAgent** | Generates optimized recommendations using historical campaign performance data |

### Collaboration Pattern

Agents operate **in parallel with shared context**:
1. RouterAgent coordinates and determines what info is available
2. Resolution agents (Goal, Audience, Budget, Schedule) execute simultaneously
3. MediaPlannerAgent synthesizes all outputs using real PostgreSQL + in-memory cache data
4. Total latency: **~3–5 seconds** with parallel execution

### Key Metrics

| Metric | Before | After |
|---|---|---|
| Campaign creation time | 15–30 minutes | 5–10 seconds |
| User inputs required | 20+ form fields | 1–3 natural language messages |
| System latency | — | ~3–5 seconds (parallel) |

### Lessons Learned

1. **Prompt engineering requires version control and rigorous testing** — treat prompts like production code
2. **Agent boundaries must balance coordination overhead vs. monolithic complexity** — too many agents = coordination tax; too few = inflexibility
3. **Providing agents with real data tools prevents hallucination** — agents accessing real PostgreSQL data outperform pure reasoning

## Quotes / Evidence

> "Creation time: Reduced from 15–30 minutes to 5–10 seconds"

> "User inputs: Dropped from 20+ form fields to 1–3 natural language messages"

> "Latency: Approximately 3–5 seconds with parallel execution"

> "Providing agents with real data tools prevents hallucination better than reasoning alone"

## Related Terms

- Autonomous Agent Teams (Level 8)
- Google Agent Development Kit (ADK)
- Vertex AI
- Router agent pattern
- Parallel agent execution
- Shared context architecture
- MediaPlanner agent
- Real-data grounding

## Relevance to Generative AI Engineer Role

This is the Level 8 case study: specialized agents collaborating on a business workflow, each with a narrow role, coordinated by a RouterAgent. Key takeaways:

1. **RouterAgent as orchestrator** — the routing pattern (one agent decides who handles what) is a reusable architectural pattern for any multi-agent system.
2. **Parallel execution is the performance unlock** — resolution agents running concurrently collapse latency from minutes to seconds. This is how you scale multi-agent systems.
3. **Narrow agent boundaries** — each agent does one thing (budget parsing, audience extraction, scheduling). Single-responsibility principle applied to agents.
4. **Real data > reasoning** — the MediaPlannerAgent queries real PostgreSQL data and in-memory caches rather than hallucinating campaign recommendations. Always ground agents in real data.
5. **ADK + Vertex AI stack** — Google's ADK is a Level 8 tool choice worth knowing alongside LangGraph, LangChain, and AWS Step Functions for agent orchestration.
