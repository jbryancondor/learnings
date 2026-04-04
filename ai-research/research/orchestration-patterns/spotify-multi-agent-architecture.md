---
source: https://engineering.atspotify.com/2026/2/our-multi-agent-architecture-for-smarter-advertising
date_accessed: 2026-04-04
published: 2026-02
author: Spotify Engineering
company: Spotify
level_mapping: [7, 8]
tags: [multi-agent, orchestration, orchestrator-worker, router-agent, parallel-execution, production, case-study, spotify, advertising]
agent: agent-4
---

## Summary
Spotify Engineering published their production multi-agent architecture for an AI-powered advertising campaign planning system (February 2026). The system uses five specialized agents coordinated by a long-running orchestration layer to translate advertiser intent (natural language) into optimized campaign configurations. This is a real-world Level 7–8 production deployment with parallel agent execution and tool-grounded outputs.

## Key Concepts

**System Overview**
The advertising system allows advertisers to describe campaigns in natural language. The multi-agent system:
1. Parses the intent
2. Resolves goals, audiences, and budget
3. Generates optimized media plans
4. All in 3–5 seconds via parallel agent execution

**The Five Specialized Agents**

| Agent | Role | Key Behavior |
|-------|------|-------------|
| **RouterAgent** | Classifies incoming messages | Analyzes what information is present; prevents unnecessary LLM calls via conditional routing |
| **GoalResolverAgent** | Maps intent to campaign objectives | Maps to: REACH, CLICKS, APP_INSTALLS |
| **AudienceResolverAgent** | Extracts targeting criteria | Uses predefined taxonomies (genre, podcast category, demographics) |
| **BudgetAgent** | Parses and normalizes budget | Handles: "$5000", "5k", "€10,000" → micro-units |
| **MediaPlannerAgent** | Generates optimized media plan | Uses historical performance data + heuristic optimization rules |

**Orchestration Layer**
A long-running orchestration layer sits above all five agents. It:
- Coordinates parallel execution (independent agents run simultaneously)
- Manages shared context (all agents consume same signals: inventory, audiences, STR, quality/risk, performance history)
- Routes outputs between agents
- Assembles final campaign configuration

**Parallel Execution Design**
GoalResolver, AudienceResolver, and Budget agents run in parallel (they're independent). MediaPlanner runs last (depends on all three). This parallelization reduces latency from ~15s (sequential) to 3–5s (parallel).

**Tool-Grounded Outputs**
Using Google ADK's FunctionTool, agents access real data rather than hallucinating:
- RouterAgent checks actual campaign state
- MediaPlannerAgent queries historical performance data
- AudienceResolverAgent looks up real taxonomy entries

Key principle: "Tools enable grounding" — LLMs reason about *what* to do; tools provide *what's actually true*.

**The Seven Optimization Rules (MediaPlanner)**
1. Cost minimization relative to historical medians
2. Delivery rate targeting near 100%
3. Budget/duration matching to proven performers
4. Demographic/interest overlap scoring
5. Budget-based scaling (1-5 recommendations based on spend)
6. [Additional rules in the article]

**Key Engineering Insight: "Prompt Engineering is Software Engineering"**
Spotify treats prompts with version control, testing, and iteration discipline — the same rigor applied to code. Prompts are not afterthoughts; they are first-class artifacts in the software development process.

**Architectural Lessons**
1. Specialization beats generalization — each agent is narrow and excellent at one thing
2. Parallel execution requires careful dependency mapping
3. Tool grounding is non-negotiable for production accuracy
4. Shared context (same underlying signals) enables coherent multi-agent output
5. Conditional routing (RouterAgent) prevents wasted LLM calls

## Quotes / Evidence

> "Campaign planning and management as a set of modular agents that share unified signals and evaluate jointly for both advertiser goals and business constraints."

> "Prompt engineering is software engineering" — treating prompts with version control, testing, and iteration was essential.

> RouterAgent "analyzes incoming user messages and determines what information is present," preventing unnecessary LLM calls through conditional execution.

> Parallel execution reducing latency to 3-5 seconds.

## Related Terms
- Orchestrator/Worker Separation
- Router Agent
- Parallel Execution
- Tool Grounding / FunctionTool
- Google ADK
- Background Agent (Level 7)
- Context Window Management
- Fan-out / Fan-in Pattern

## Relevance to Generative AI Engineer Role
The Spotify case study is the canonical 2026 production example of Level 7 multi-agent architecture. Key takeaways for a GenAI engineer: (1) design agents to be specialized and independently testable; (2) invest in parallel execution design for latency-sensitive workflows; (3) ground agent outputs in real tools rather than relying on LLM knowledge; (4) treat prompt design with software engineering discipline. The RouterAgent pattern (conditional routing to prevent unnecessary LLM calls) is particularly applicable to cost-sensitive production deployments.
