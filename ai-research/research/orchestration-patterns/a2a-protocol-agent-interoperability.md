---
source: https://developers.googleblog.com/en/a2a-a-new-era-of-agent-interoperability/
date_accessed: 2026-04-04
published: 2025-04
author: Google (donated to Linux Foundation)
company: Google / Linux Foundation
level_mapping: [8]
tags: [a2a, agent-to-agent, protocol, interoperability, multi-agent, autonomous-teams, communication-standard, google]
agent: agent-4
---

## Summary
The **Agent2Agent (A2A) Protocol** is an open communication standard introduced by Google in April 2025 and subsequently donated to the Linux Foundation. It provides a common language for AI agents to communicate with each other across different frameworks and vendors. A2A is the infrastructure-level enabler for Level 8 Autonomous Agent Teams — allowing agents built with LangGraph, AutoGen, CrewAI, or custom frameworks to interoperate without bespoke integration code.

## Key Concepts

**Core Purpose**
A2A solves the interoperability problem: agents built by different teams, using different frameworks, from different vendors cannot coordinate without a shared protocol. A2A provides:
- Standardized task lifecycle (submitted → working → input-required → completed/failed)
- Authentication/authorization (enterprise-grade, parity with OpenAPI schemes)
- Discovery mechanism (agents advertise capabilities)
- Communication primitives (message passing, task delegation, result return)

**Task Lifecycle Model**
Every A2A interaction is structured as a Task with a unique ID and defined state progression:

```
submitted → working → [input-required] → completed
                  ↘                    ↗
                    failed
```

Tasks support multi-turn processing — the `input-required` state allows an agent to pause and request additional information (from human or another agent) before continuing.

**Key Protocol Features**
- **Task Management**: Unique IDs, lifecycle states, multi-turn support
- **Security**: Enterprise authentication/authorization aligned with OpenAPI schemes
- **Discovery**: Agent capability advertisement (what tasks can this agent perform?)
- **gRPC Support** (v0.3, July 2025): High-performance binary transport alongside HTTP/JSON
- **Signed Security Cards** (v0.3): Cryptographically verifiable agent identity

**Industry Adoption**
Launched with 50+ technology partners including:
- **Frameworks**: LangChain, MongoDB
- **Platforms**: Atlassian, Box, Salesforce, SAP, ServiceNow, Workday, PayPal, Intuit, Cohere
- **Service Providers**: Accenture, BCG, Capgemini, Cognizant, Deloitte, McKinsey, PwC, TCS, Wipro

By July 2025 (v0.3): 150+ supported organizations.

**Linux Foundation Governance**
Google donated A2A to the Linux Foundation for neutral governance — similar to how Kubernetes, Linux, and other foundational infrastructure became community-governed. This signals A2A's positioning as critical infrastructure for the AI agent ecosystem, not a Google-proprietary tool.

**A2A vs. MCP (Model Context Protocol)**
A2A and Anthropic's MCP serve different purposes:
- **MCP**: Agent ↔ Tool/Resource communication (how an agent accesses external data and tools)
- **A2A**: Agent ↔ Agent communication (how agents coordinate with each other)

These are complementary protocols. A production Level 8 system would use both: MCP for tool access within each agent, A2A for coordination between agents.

**Connection to Orchestrator/Worker Pattern**
A2A provides the communication layer that makes Orchestrator/Worker patterns possible across organizational and framework boundaries. An orchestrator agent can delegate tasks to worker agents built by different teams using A2A, without needing custom integration code for each worker.

## Quotes / Evidence

> "Enabling agents to interoperate with each other, even if they were built by different vendors or in a different framework, will increase autonomy and multiply productivity gains, while lowering long-term costs."

> A task has a unique ID and progresses through defined states: "submitted, working, input-required, completed, failed. Tasks are useful for multi-turn processing or long-running agent-to-agent collaboration."

From Linux Foundation announcement: "Secure, Intelligent Communication Between AI Agents"

## Related Terms
- MCP (Model Context Protocol)
- Orchestrator/Worker Separation
- Autonomous Agent Teams (Level 8)
- Task Lifecycle Management
- gRPC
- OpenAPI
- Agent Discovery
- Interoperability Standard

## Relevance to Generative AI Engineer Role
A2A is the emerging standard for production Level 8 multi-agent communication. A GenAI engineer designing autonomous agent teams should: understand the A2A task lifecycle, evaluate whether their framework supports A2A (LangChain, many platforms do), and design agent interfaces as A2A-compatible from the start. The distinction between A2A (agent-to-agent) and MCP (agent-to-tool) is a critical architectural concept — conflating them leads to improper system design.
