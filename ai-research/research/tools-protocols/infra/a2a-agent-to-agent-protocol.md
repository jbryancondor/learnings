---
source: https://www.linuxfoundation.org/press/linux-foundation-launches-the-agent2agent-protocol-project-to-enable-secure-intelligent-communication-between-ai-agents
date_accessed: 2026-04-04
published: 2025-06-01
author: Google (donated) / Linux Foundation
company: Google / Linux Foundation
level_mapping: [8]
tags: [a2a, agent-to-agent, protocol, multi-agent, interoperability, aaif, linux-foundation, google]
agent: agent-3b
---

## Summary
Agent2Agent (A2A) is an open protocol created by Google for secure, standardized communication and interoperability between AI agents. Announced in April 2025 with 100+ supporting companies, it was donated to the Linux Foundation in June 2025. Where MCP connects agents to tools/data, A2A connects agents to other agents — enabling multi-agent systems where specialized agents from different vendors, frameworks, and platforms can discover each other's capabilities, exchange information securely, and coordinate complex tasks. A2A and MCP together form the two-layer interoperability stack for modern agentic AI.

## Key Concepts

### Core Purpose
- **Agent Discovery**: Agents can find and understand other agents' capabilities at runtime
- **Secure Communication**: Encrypted, authenticated agent-to-agent message passing
- **Task Delegation**: Agents can delegate subtasks to specialist agents across vendor/framework boundaries
- **Interoperability**: Works regardless of which framework built each agent (LangGraph, CrewAI, AutoGen, Claude Agent SDK, etc.)

### Governance and Adoption
- **April 2025**: Google launches A2A with 100+ company support
- **June 2025**: Linux Foundation formally launches the Agent2Agent project
- **Founding members**: Amazon Web Services, Cisco, Google, Microsoft, Salesforce, SAP, ServiceNow
- Google donated the protocol specification, SDKs, and developer tooling to Linux Foundation
- **AAIF (Agentic AI Foundation)**: Separate but related — co-founded by OpenAI, Anthropic, Block under Linux Foundation; MCP also governed here

### MCP vs. A2A: The Full Stack
| Dimension | MCP | A2A |
|-----------|-----|-----|
| Purpose | Agent ↔ Tool/Data | Agent ↔ Agent |
| Direction | Agent calls tool | Agent delegates to agent |
| Origin | Anthropic (Nov 2024) | Google (Apr 2025) |
| Governance | Linux Foundation AAIF | Linux Foundation (separate project) |
| Layer | Infrastructure | Orchestration |

### Technical Model
- Agents expose an "agent card" — a metadata manifest describing capabilities, input/output schemas, and authentication requirements
- Communication via HTTP + JSON-based messaging
- Task lifecycle: create → update → complete/error with streaming support
- Authentication: OAuth2, API keys, or custom schemes

### Production Use Cases
- A coding agent (e.g., Claude Code) delegating to a specialized database agent
- A research agent spawning specialist agents for different domains
- Cross-vendor workflows: LangGraph orchestrator + CrewAI sub-agents + Claude Agent SDK workers
- Enterprise multi-agent pipelines with audit trails per agent interaction

## Quotes / Evidence
> "A2A empowers developers to build agents that seamlessly interoperate, regardless of platform, vendor or framework." — Linux Foundation announcement, 2025

> "A2A and the Agentic AI Foundation (AAIF) are two new standards developing to ensure agents from multiple sources work together, reflecting a recognition that they need multi-level standards defining how agents from different vendors interoperate." — Blocks and Files, Dec 2025

> "By providing a common language for AI agents to discover each other's capabilities, securely exchange information, and coordinate complex tasks, the A2A protocol is paving the way for a new era of more powerful, collaborative, and innovative AI applications." — Linux Foundation, 2025

## Related Terms
- MCP (Model Context Protocol) — complementary standard
- AAIF (Agentic AI Foundation)
- Agent Card (capability manifest)
- Multi-Agent Systems
- mcp-agent (framework that uses both)
- CrewAI, AutoGen, LangGraph (frameworks that implement A2A)

## Relevance to Generative AI Engineer Role
At Level 8, building autonomous agent teams requires understanding A2A as the interoperability protocol. A Gen AI Engineer designing multi-agent systems needs to: expose agent cards for specialist agents, implement A2A routing in orchestration layers, understand the trust/auth model for cross-agent calls, and choose when to use A2A (cross-vendor delegation) vs. internal framework mechanisms (e.g., LangGraph subgraphs). A2A is the enabler of truly heterogeneous multi-agent architectures.
