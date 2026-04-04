---
source: https://en.wikipedia.org/wiki/Model_Context_Protocol
date_accessed: 2026-04-04
published: 2024-11-01
author: Anthropic (donated to Linux Foundation AAIF Dec 2025)
company: Anthropic / Linux Foundation AAIF
level_mapping: [5]
tags: [mcp, protocol, tools, api, integration, aaif, linux-foundation]
agent: agent-3b
---

## Summary
Model Context Protocol (MCP) is an open standard introduced by Anthropic in November 2024 that standardizes how AI systems (LLMs, agents) integrate and share data with external tools, systems, and data sources. It functions as a universal connector — rather than embedding raw context into prompts, MCP allows models to access information from connected tools including file systems, APIs, documentation platforms, issue trackers, and development environments on-demand. As of December 2025, Anthropic donated MCP to the Agentic AI Foundation (AAIF), a directed fund under the Linux Foundation, co-founded by Anthropic, Block, and OpenAI with support from Google, Microsoft, AWS, Bloomberg, and Cloudflare.

## Key Concepts

### Core Architecture
- **MCP Servers**: Expose tools and data sources; run locally or remotely
- **MCP Clients**: AI models/agents that connect to servers to retrieve context
- **Transport Layer**: stdio (local) or HTTP+SSE/WebSocket (remote)
- **Tool Calling**: Structured function calls through MCP that return typed results

### Ecosystem Scale (2026)
- 97 million monthly SDK downloads as of February 2026
- 66,000 server invocations per month across 844 active users as of early 2025
- Every major AI platform (OpenAI, Google, Microsoft, AWS) supports MCP
- Pinterest, Cloudflare, and other enterprises deploying at production scale
- MCP described as "growing faster than any developer tool standard since Docker"

### Registry & Discovery
- **MCP Registry** (launched Sept 2025): Open catalog and API for indexing and discovering MCP servers; single source of truth for available servers, supports public and private sub-registries
- **PulseMCP**: Community registry and discovery platform, major contributor to official registry alongside Anthropic, GitHub, and Microsoft
- Registry stores metadata (not code) — actual packages live on npm, PyPI, Docker Hub
- Namespace auth via reverse DNS format (e.g., `io.github.username/server-name`)

### 2026 Roadmap Priorities
- **Stateless sessions**: Evolving transport model so servers scale horizontally without holding state
- **Discoverable metadata**: Standard `.well-known` format for server capabilities without live connection
- **Enterprise features**: Audit trails, SSO-integrated auth, gateway behavior, config portability
- **Spec Enhancement Proposals (SEPs)**: Formal community governance process
- **Working Groups**: Community-driven protocol evolution under AAIF

### MCP vs. A2A
- MCP: connects AI to tools, APIs, data sources (agent ↔ tool)
- A2A: connects agents to other agents (agent ↔ agent)
- Both governed under Linux Foundation AAIF — designed as complementary standards

## Quotes / Evidence
> "MCP servers reached 66,000 invocations per month across 844 active users, saving roughly 7,000 hours per month." — Search results, early 2025 data

> "The MCP market is expected to reach $1.8B in 2025, driven by strong demand from highly regulated fields like healthcare, finance, and manufacturing." — CData, 2026

> "Running MCP at scale has surfaced gaps: stateful sessions fight with load balancers, horizontal scaling requires workarounds, and there's no standard way for a registry or crawler to learn what a server does without connecting to it." — MCP 2026 Roadmap

## Related Terms
- Tool Calling / Function Calling
- A2A (Agent-to-Agent Protocol)
- AAIF (Agentic AI Foundation)
- MCPM (MCP Package Manager)
- MCP Registry / PulseMCP
- Claude Code Skills
- Claude Desktop, Cursor, Windsurf (MCP clients)

## Relevance to Generative AI Engineer Role
At Level 5, a Gen AI Engineer works directly with MCP to connect AI agents to external tools and data. Practical skills include: choosing/configuring MCP servers (filesystem, GitHub, databases, APIs), building custom MCP servers, understanding the client/server transport model, and using registries like PulseMCP to discover available servers. MCP is now the de facto standard for agent-tool integration — understanding it is non-negotiable at this level.
