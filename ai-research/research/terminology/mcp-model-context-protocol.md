---
source: https://www.anthropic.com/news/model-context-protocol
date_accessed: 2026-04-04
published: 2024-11-01
author: Anthropic / Linux Foundation AAIF
company: Anthropic
level_mapping: [Level 5 - MCP & Skills]
tags: [MCP, protocol, standard, context, integration]
agent: agent-5
---

## Summary
The Model Context Protocol (MCP) is an open standard introduced by Anthropic in November 2024 that standardizes how AI systems integrate with external tools, data sources, and services. MCP solves the "N×M integration problem"—instead of building custom connectors for each AI model and tool combination, MCP provides a universal interface. Now adopted by OpenAI and Google, MCP is becoming industry infrastructure for grounding AI systems in external context.

## Key Concepts
- **Open Standard**: Vendor-neutral protocol maintained by Anthropic and Linux Foundation AAIF
- **Universal Interface**: Single protocol for all model-to-tool integrations
- **N×M Problem**: Eliminates custom connectors between N models and M tools
- **Three Operations**: Read files, execute functions, handle contextual prompts
- **Tool Discovery**: Standardized way for tools to register capabilities
- **Context Sharing**: Unified mechanism for passing context between models and tools
- **Server Architecture**: Tools implement MCP servers; models implement clients
- **Industry Adoption**: OpenAI, Google DeepMind, and others now support MCP

## Quotes / Evidence
"MCP standardizes the way AI systems integrate with external tools, systems, and data sources, solving the N×M integration problem." — Anthropic November 2024

"Before MCP, developers built custom connectors for each AI model and tool combination. MCP provides a universal interface eliminating this inefficiency." — Protocol motivation

## Related Terms
- Tool Use / Function Calling
- Skills / MCP Skills
- Agent Framework
- Model Context Protocol
- External Integration

## Relevance to Generative AI Engineer Role
MCP is foundational infrastructure for modern AI systems. You'll implement MCP servers to expose tools and data sources to models, design client interfaces for model access, and orchestrate tool ecosystems. MCP adoption determines your system's interoperability and scalability.

Sources:
- [Anthropic: Model Context Protocol Announcement](https://www.anthropic.com/news/model-context-protocol)
- [MCP Specification](https://modelcontextprotocol.io/specification/2025-11-25)
- [Google Cloud: What is MCP](https://cloud.google.com/discover/what-is-model-context-protocol)
