---
source: https://martinfowler.com/articles/exploring-gen-ai/humans-and-agents.html
date_accessed: 2026-04-04
published: 2025-01-01
author: Martin Fowler & Thoughtworks
company: Thoughtworks
level_mapping: [Level 6 - Harness Engineering]
tags: [evaluation, review, quality-assurance, automation, judgment-free]
agent: agent-5
---

## Summary
"Evaluation over review" is a practice shift where AI-generated code/content is judged against specifications and automated criteria rather than human code review. Instead of humans reading diffs and approving/rejecting based on judgment, systems evaluate outputs against explicit specifications, tests, and automated metrics. This approach scales better, removes subjectivity, and shifts review from "is this good?" to "does this meet the spec?" Evaluation is about facts (does it pass tests?); review is about judgment (do I like it?).

## Key Concepts
- **Specification-Based**: Evaluate against explicit spec, not human opinion
- **Automated Metrics**: Use tests, linting, performance checks, not reviewer approval
- **Judgment-Free**: Remove subjective approval gates
- **Scalability**: Evaluation scales with automation; review bottlenecks on humans
- **Reproducibility**: Same specs always produce same evaluation; review depends on reviewer
- **Shift Left**: Problems caught by evaluation, not human gatekeeping
- **Faster Iteration**: Eliminate review delays; continuous evaluation feedback
- **LLM Judge Integration**: Use LLM judges for quality dimensions not easily automated

## Quotes / Evidence
"Evaluation is about facts (does it meet the spec?); review is about judgment (do I like it?)." — Martin Fowler

"Evaluation scales with automation. Review bottlenecks on humans. Shift away from review and toward evaluation for production systems." — Practice principle

"Explicit specifications enable automated evaluation. Judgment-based review slows iteration and masks subjective preferences as objective standards." — Design philosophy

## Related Terms
- Specification-Driven Development (SDD)
- LLM-as-Judge
- Harness Engineering
- Regenerative Architecture
- Autonomous Development Loop

## Relevance to Generative AI Engineer Role
Evaluation over review is your path to sustainable AI-augmented development. You'll design explicit specifications, implement evaluation pipelines, automate quality checks, and shift from "did a human approve it?" to "does it meet the specification?" This enables rapid iteration with AI agents while maintaining quality standards.

Sources:
- [Martin Fowler: Humans and Agents](https://martinfowler.com/articles/exploring-gen-ai/humans-and-agents.html)
- [Thoughtworks: Evaluation Over Review Practices](https://www.thoughtworks.com/insights)
- [LinearB: AI Code Review Evaluation](https://linearb.io/blog/ai-code-review)
