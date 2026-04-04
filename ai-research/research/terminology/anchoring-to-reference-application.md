---
source: https://martinfowler.com/articles/exploring-gen-ai/anchoring-to-reference.html
date_accessed: 2026-04-04
published: 2025-01-01
author: Martin Fowler & Thoughtworks
company: Thoughtworks
level_mapping: [Level 3 - Context Engineering]
tags: [reference-application, consistency, drift-detection, service-templates, agents]
agent: agent-5
---

## Summary
Anchoring coding agents to a reference application is a pattern for maintaining code consistency. Instead of providing static prompt examples, you expose a live, compilable reference codebase to agents via an MCP server. Agents detect drift between generated code and the reference, and the codebase serves as the single source of truth for architectural and stylistic patterns. Commits document intentional changes; diffs guide drift detection.

## Key Concepts
- **Reference Application**: Live, compilable example implementation (service template)
- **MCP Server Integration**: Exposes reference code and commit history to agents
- **Drift Detection**: Agents identify divergence between generated and reference code
- **Commit Messaging**: Describe intentional changes, enabling scoped drift detection
- **Template Maintenance**: Keep reference application current as standards evolve
- **Scope Control**: Using commits to control which drift types matter
- **Consistency Enforcement**: Agents repair divergence based on reference patterns
- **Single Source of Truth**: Reference app replaces scattered documentation

## Quotes / Evidence
"Maintaining code samples in a reference application project that you can compile and run makes it much easier to provide AI with compilable, consistent samples." — Martin Fowler, Thoughtworks

"Once generated code is extended and maintained, codebases often drift from the reference application. Using commits to communicate drift scope helps avoid irrelevant comparisons." — Implementation guidance

"MCP servers expose both reference templates and commit diffs, enabling agents to detect drift and propose repairs." — Technical pattern

## Related Terms
- Context Engineering
- Agent Framework
- Specification-Driven Development (SDD)
- Regenerative Architecture
- Tool Use (MCP)

## Relevance to Generative AI Engineer Role
You'll create and maintain reference applications for AI agents, establishing architectural baselines that agents follow. This is how you move from "whatever the AI generates" to "generated code that matches our standards." Reference applications are documentation and specification combined—the most effective way to share architectural intent with AI systems.

Sources:
- [Martin Fowler: Anchoring to Reference Application](https://martinfowler.com/articles/exploring-gen-ai/anchoring-to-reference.html)
- [Thoughtworks: Anchoring Agents Pattern](https://www.thoughtworks.com/radar/techniques/anchoring-coding-agents-to-a-reference-application)
- [Chip Huyen: AI Engineering Reference Apps](https://github.com/chiphuyen/aie-book)
