---
source: https://martinfowler.com/articles/exploring-gen-ai/sdd-3-tools.html
date_accessed: 2026-04-04
published: 2025-01-01
author: Martin Fowler & Thoughtworks
company: Thoughtworks
level_mapping: [Level 4 - Compounding Engineering]
tags: [spec-driven-development, formal-specifications, AI-code-generation, machine-readable, discipline]
agent: agent-5
---

## Summary
Spec-driven development (SDD) is a software engineering methodology where a formal, machine-readable specification serves as the authoritative source of truth. Specifications are detailed enough to generate code, validate outputs, and derive tests automatically. SDD emerged in 2025 as a response to hallucinations and inconsistencies in AI code generation, emphasizing explicit, reviewable, and evolvable technical decisions over conversational iteration.

## Key Concepts
- **Formal Specification**: Machine-readable, not just natural language documentation
- **Single Source of Truth**: Specification defines all aspects—behavior, contracts, constraints
- **Automated Code Generation**: Detailed specs enable AI to generate correct implementations
- **Automated Testing**: Specifications drive test generation and validation
- **Verifiable Contracts**: Input/output mappings, preconditions, postconditions, invariants
- **Explicit Constraints**: Define what can't happen—not just what should
- **State & Logic**: Formal description of sequential logic and state machines
- **Integration Contracts**: Clear API boundaries and expected behavior

## Quotes / Evidence
"SDD uses well-crafted software requirement specifications as prompts, aided by AI coding agents, to generate executable code." — Thoughtworks

"Unlike regular documentation, SDD specifications are formal, machine-readable artifacts that can drive code generation, validation, and testing automatically." — Industry practice

"SDD may lack the visibility of vibe coding, but it's one of the most important practices to emerge in 2025." — Martin Fowler analysis

## Related Terms
- Compounding Engineering
- Regenerative Architecture
- Evaluation Over Review
- Amazon Kiro
- Prompt Engineering

## Relevance to Generative AI Engineer Role
SDD represents a maturation from prompting to engineering discipline. You'll craft specifications that guide AI systems reliably, design testing frameworks to validate generated code, and build evaluation pipelines independent of code artifacts. This is how you move from "did it work this time?" to "is it correct by specification?"

Sources:
- [Martin Fowler: Understanding SDD Tools](https://martinfowler.com/articles/exploring-gen-ai/sdd-3-tools.html)
- [Thoughtworks: Spec-Driven Development 2025](https://thoughtworks.medium.com/spec-driven-development-d85995a81387)
- [Augment Code: SDD Guide](https://www.augmentcode.com/guides/what-is-spec-driven-development)
