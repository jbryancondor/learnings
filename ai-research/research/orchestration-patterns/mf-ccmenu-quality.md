---
source: https://martinfowler.com/articles/exploring-gen-ai/ccmenu-quality.html
date_accessed: 2026-04-04
published: 2026-01
author: Martin Fowler
company: Thoughtworks
level_mapping: [6, 7]
tags: [orchestration, code-quality, internal-quality, evaluation, agent-review, technical-debt]
agent: agent-4
---

## Summary
MF #22 in the Exploring Gen AI series. Fowler evaluates internal code quality when using AI agents (Claude with Sonnet 4.5) to build a macOS menu bar app (CCMenu). The article demonstrates that AI agents can generate functionally correct code that simultaneously introduces non-idiomatic patterns, semantic degradation, and unnecessary complexity — issues only detectable by experienced human reviewers.

## Key Concepts

**Internal Quality vs. External Behavior**
AI agents prioritize making code work (passing tests, compiling, shipping features) over internal quality attributes like idiomaticity, maintainability, and adherence to language conventions. Internal quality is the sustainability variable — poor internal quality causes velocity to collapse over time.

**Semantic Degradation**
Agents replace explicit language semantics with implicit conventions. Example: using empty strings (`?? ""`) as null proxies instead of Swift's Optional type — works functionally, but removes type system guarantees and self-documentation, introducing hidden bugs.

**Categories of Agent Quality Failure**
1. Unnecessary complexity — introducing unneeded caching, duplicate URL construction logic
2. Semantic degradation — replacing type-safe idioms with workaround patterns
3. Missing non-obvious functionality — overlooking macOS defaults system for testing
4. Documentation hallucination — inventing API response structures not in docs

**Human Oversight as Quality Gate**
Experienced developers must redirect agents toward proper solutions. Agents lack the context to understand why a language provides certain constructs (e.g., Optionals in Swift) and will substitute something that "works." The developer's role shifts to architectural review and quality enforcement, not implementation.

**Implication for Harness Engineering**
Quality checks must be encoded in the harness (not just left to human review), otherwise agents will consistently produce technically functional but internally degraded code at scale.

## Quotes / Evidence

> "I'd argue, though, that internal quality is crucial for development to continue at a sustainable pace over years, rather than collapse under its own weight."

> "The AI ignored this and introduced new semantics...This is not idiomatic, not self-documenting, unsupported by Swift's type system."

## Related Terms
- Internal quality / External behavior
- Semantic degradation
- Idiomatic code
- Technical debt accumulation
- Harness engineering
- LLM-as-Judge (quality evaluation)
- Human-on-the-loop

## Relevance to Generative AI Engineer Role
Understanding the gap between functional correctness and internal quality is critical for designing agent harnesses with effective quality gates. A GenAI engineer must encode quality criteria (style guides, idiomatic patterns, architectural constraints) as machine-checkable specifications rather than relying solely on human review — which cannot scale to agent output velocity.
