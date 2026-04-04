---
source: https://www.infoq.com/news/2025/12/qcon-ai-linkedin/
date_accessed: 2026-04-04
published: 2025-12-01
author: Prince Valluri, Karthik Ramgopal (LinkedIn Engineering)
company: LinkedIn
level_mapping: [3, 6, 7]
tags: [linkedin, ai-agent-platform, level-3, level-6, level-7, context-engineering, governance, observability, background-coding-agents]
agent: agent-2
---

## Summary

At QCon AI New York 2025, LinkedIn engineers Prince Valluri and Karthik Ramgopal described LinkedIn's internal AI agent platform — built to support AI agents at scale in a "governed execution environment designed for large, long-lived engineering organizations." LinkedIn is running **background coding agents that asynchronously translate specifications into pull requests** (Level 7) and analytics agents that enable engineers and business users to query data without SQL. The platform's key architectural insight: treat agents as participants in a governed system, not isolated tools.

## Key Concepts

### Core Architecture Principle

LinkedIn separates **human intent from machine execution** using structured specifications instead of free-form prompts. This separation enhances:
- Agent observability (what is the agent trying to do?)
- Interoperability (different agents can consume the same spec)
- Human accountability (humans approve the spec before execution)

### Context Engineering as First Priority

> "Many agent failures stem from missing or stale context, making context engineering a more critical investment than model selection."

LinkedIn's platform prioritizes context management over model optimization — a counter-intuitive but evidence-backed finding.

### Production Agents at LinkedIn

| Agent Type | Function | Level |
|---|---|---|
| Background Coding Agents | Asynchronously translate specifications into pull requests | 7 |
| Analytics Agents | Enable engineers/business users to query data in natural language | 7 |
| Governance Layer | Monitors agent actions, ensures human accountability | 6 |

### Governance vs. Isolation

LinkedIn explicitly rejects "isolated tools" in favor of a "governed execution environment." Key implications:
- Agents have defined permissions, scopes, and audit trails
- Long-running agents need observability across multi-day execution
- Interoperability is a design requirement, not an afterthought

### Context Engineering Priority Ranking

LinkedIn's finding: **context > model**. The platform invests more in:
1. Structured specs (replacing free-form prompts)
2. Stale context detection
3. Missing context identification

...than in model selection or fine-tuning.

## Quotes / Evidence

> "Many agent failures stem from missing or stale context, making context engineering a more critical investment than model selection."

> "Background coding agents that asynchronously translate specifications into pull requests"

> "Analytics agents that enable engineers and business users to query data"

> "Treat AI agents not as isolated tools, but as participants in a governed execution environment"

> "Using structured specifications within a robust orchestration layer to enhance agent observability and interoperability while ensuring human accountability"

## Related Terms

- Context Engineering (Level 3)
- Harness Engineering (Level 6)
- Background Coding Agents (Level 7)
- Governed execution environment
- Structured specifications
- Agent observability
- Long-lived agent orchestration
- Interoperability layer

## Relevance to Generative AI Engineer Role

LinkedIn's approach represents the enterprise pattern for deploying agents at scale within a large organization:

1. **Governance is Level 6 infrastructure** — the governed execution environment is the harness that makes Level 7 agents safe to run at enterprise scale. You can't skip it.
2. **Structured specs > free-form prompts** — LinkedIn's move from prompts to structured specifications is a maturity signal. Once agents are in production, the spec becomes the contract.
3. **Context engineering > model selection** — this is LinkedIn's key finding. Spending 10x more on context management than on model choice is the right investment ratio.
4. **Observability for multi-day agents** — when agents run for hours or days, you need observability tooling that goes beyond "did it finish?" Understanding agent state mid-execution is a hard engineering problem.
