---
source: https://martinfowler.com/articles/exploring-gen-ai/sdd-3-tools.html
date_accessed: 2026-04-04
published: 2025-10-15
author: Birgitta Böckeler
company: Thoughtworks
level_mapping: [4]
tags: [sdd, spec-driven-development, amazon-kiro, github-spec-kit, tessl, claude-code, compounding-engineering, level-4]
agent: agent-3a
---

## Summary

Level 4 — Compounding Engineering — is where AI-assisted development transcends individual coding tasks and becomes a **systematic methodology**. Spec-Driven Development (SDD) makes the specification the primary artifact; code becomes its generated output. This level introduces formal workflow tooling that governs how AI agents plan, specify, and implement features.

Three principal tools define this space (2025):
- **Amazon Kiro** — VS Code fork with spec-driven workflow built in; powered by Claude Sonnet
- **GitHub Spec-Kit** — CLI-based specification framework for any coding assistant
- **Tessl** — Agent Enablement Platform; spec-centric with bidirectional spec↔code sync (closed beta)

Claude Code also belongs here as the compounding agent that executes within SDD workflows.

## Key Concepts

### What Spec-Driven Development (SDD) Is

> "Writing a 'spec' before writing code with AI; the spec becomes the source of truth for the human and the AI." — Birgitta Böckeler, Thoughtworks (2025)

SDD is the evolution of TDD (Test-Driven Development) and BDD (Behavior-Driven Development) for the AI era. Core inversion: **specifications are the primary artifact; code is generated from them.**

**Three levels of SDD** (Böckeler's taxonomy):
1. **Spec-first** — Spec written before AI-assisted development; code is the output
2. **Spec-anchored** — Spec maintained after implementation; drives future evolution
3. **Spec-as-source** — Humans edit only specs, never code directly; code fully generated

**Why SDD now?** Three conditions aligned in 2025:
1. AI reliably translates natural language into working code
2. Software complexity demands systematic alignment with original intent
3. Rapid iteration requires pivots without manual propagation through documentation

**Warning — MDD parallel**: Böckeler warns SDD risks repeating Model-Driven Development (MDD) failures: inflexibility, overhead, tooling lock-in. LLM capabilities reduce some constraints but the risk remains.

### Amazon Kiro

**What it is**: VS Code fork, powered by Claude Sonnet (Anthropic), Amazon product

**Workflow** (three markdown documents):
1. **Requirements** (`requirements.md`) — User stories with acceptance criteria; AI-generated from natural language
2. **Design** (`design.md`) — Technical design with diagrams, data schemas, architecture decisions
3. **Tasks** (`tasks.md`) — Sequenced, trackable implementation tasks; AI generates from design

**Steering files** (persistent context, not per-spec):
- `product.md` — Product vision and business context
- `tech.md` — Tech stack, dependencies, architectural constraints
- `structure.md` — Codebase structure and conventions

**Key feature**: Spec stays synced with evolving codebase — developer can ask Kiro to update specs after code changes, or update specs to trigger task regeneration

**Task execution**: Real-time status updates as tasks move in-progress → complete

**Strengths** (per Böckeler and practitioners):
- Best for complex features needing upfront design clarity
- Spec-first approach naturally prevents vibe coding drift
- Integration of spec management and code execution in one tool

**Weaknesses**:
- Overly verbose for small problems; poor scaling across problem sizes
- 50 interactions/month in early access (significant friction)
- Specification overhead may exceed code review time for simple tasks

**Positioning**: Cursor wins for fast iteration; Kiro wins for complex features needing upfront design clarity

### GitHub Spec-Kit

**What it is**: CLI-based specification framework, works with any coding assistant (Cursor, Claude Code, Copilot, Windsurf, Gemini CLI)

**Source**: `github.com/github/spec-kit` (October 2025)

**Workflow** (four phases):
1. **Constitution** — Immutable development principles (Nine Articles): Library-First, CLI Interface Mandate, Test-First Imperative, Simplicity/Anti-Abstraction, Integration-First Testing
2. **Specify** (`/speckit.specify`) — Creates feature spec with branch management, template population
3. **Plan** (`/speckit.plan`) — Generates implementation plan with constitutional compliance checking
4. **Tasks** (`/speckit.tasks`) — Derives executable task list from plan and design documents

**Constitutional Foundation** — Nine Articles (selected):
- Library-First Principle: prefer existing libraries over custom implementation
- Test-First Imperative: tests before implementation
- Simplicity and Anti-Abstraction: minimum complexity for current task
- Integration-First Testing: test against real systems, not mocks

**Key quote**: "Specs become the shared source of truth. When something doesn't make sense, you go back to the spec."

**Template-driven quality**: Structured templates constrain LLM output by:
- Preventing premature implementation details
- Forcing `[NEEDS CLARIFICATION]` markers for ambiguity
- Enforcing test-first thinking
- Requiring simplicity justification

**Concern** (Böckeler): Creates extensive markdown files; appears spec-first only, not truly spec-anchored — spec does not automatically stay synced with code changes

### Tessl

**What it is**: Agent Enablement Platform; $125M funding (Index Ventures, Accel, GV, boldstart)

**Products** (launched 2025):
- **Tessl Framework** (closed beta): Spec-centric development; specs live in codebase as long-term memory; uses `@generate` and `@test` tags; generates code from specs; bidirectional sync (spec ↔ code)
- **Tessl Spec Registry** (open beta): 10,000+ specs explaining how to use external libraries; prevents API hallucinations and version mixups

**Key differentiators** (vs Kiro and Spec-Kit):
- **Only tool targeting spec-anchored AND spec-as-source** (not just spec-first)
- **1:1 spec-to-file mapping**: Each spec file directly corresponds to an implementation file
- **Bidirectional sync**: Specs can regenerate code; code changes can update specs
- **Anti-hallucination**: Spec Registry provides verified patterns for popular libraries

**Context**: AWS validated the SDD thesis with Kiro (July 2025); GitHub released Spec-Kit (October 2025); Tessl is the venture-backed pure-play SDD company betting the entire product on this paradigm

**Status as of April 2026**: Framework in closed beta; Registry in open beta

### Thoughtworks / Liu Shangqi Synthesis (December 2025)

From "Spec-Driven Development: Unpacking 2025's New Engineering Practices":

**Definition**: "A development paradigm that uses well-crafted software requirement specifications as prompts, aided by AI coding agents, to generate executable code." — Liu Shangqi, Technology Director, APAC

**What makes good specs**:
- Domain-oriented language (not technical jargon)
- Given/When/Then structures (BDD-style acceptance criteria)
- Balance completeness with conciseness
- Prioritize clarity and determinism
- Semi-structured formats reduce AI hallucinations

**Key warning**: "Spec drift and hallucination are inherently difficult to avoid. We still need highly deterministic CI/CD practices to ensure software quality and safeguard our architectures." — Liu Shangqi

**Distinction from waterfall**: SDD enables shorter feedback cycles, not extended delays; the spec is living and agent-driven

## Quotes / Evidence

> "The specification becomes the primary artifact. Code becomes its expression in a particular language and framework." — GitHub Spec-Kit documentation

> "Specs become the shared source of truth. When something doesn't make sense, you go back to the spec." — GitHub Spec-Kit

> "Spec-driven development is a workflow where your AI coding agent gathers requirements and writes specifications before writing any code. You review and approve the specs, then the agent implements them." — Tessl, 2025

> "AWS validated this thesis with the July launch of Kiro, an agentic IDE built around spec-driven development. Meanwhile, GitHub released Spec Kit in October, bringing spec-driven workflows to Copilot, Claude Code, Gemini CLI, Cursor, and Windsurf." — Tessl blog, 2025

> "Kiro wins for complex features needing upfront design clarity. Downside: 50 interactions/month runs out fast; spec overhead is friction for simple tasks; still early-access." — OpenAIToolsHub review

> "The spec becomes the source of truth for the human and the AI." — Birgitta Böckeler, Thoughtworks, 2025

## Related Terms

- **SDD (Spec-Driven Development)** — methodology where specs are primary artifacts; code is generated
- **TDD / BDD** — predecessors to SDD; TDD = test-first, BDD = behavior-first, SDD = specification-first
- **Constitution** — GitHub Spec-Kit's immutable development principles (Nine Articles)
- **Steering files** — Kiro's persistent context documents (product.md, tech.md, structure.md)
- **Spec Registry** — Tessl's library of 10,000+ verified library usage specs
- **Spec drift** — when code diverges from its specification over time (the central SDD problem)
- **Spec-as-source** — the most ambitious SDD mode: humans never write code directly
- **MDD (Model-Driven Development)** — 1990s predecessor; cautionary tale about spec overhead
- **Vibe coding** — the anti-pattern SDD is designed to correct: AI-assisted coding without upfront planning
- **Constitutional AI (Spec context)** — Spec-Kit's use of "constitution" (immutable rules) mirrors Anthropic's Constitutional AI concept

## Relevance to Generative AI Engineer Role

Level 4 is the frontier for a Generative AI Engineer in 2025–2026. It represents the transition from **using AI tools** to **engineering AI-driven development pipelines**.

Key competencies:
1. **SDD methodology**: Understanding when to apply spec-first, spec-anchored, or spec-as-source approaches based on problem complexity and team maturity
2. **Tool selection**: Kiro for AWS shops needing IDE integration; Spec-Kit for CLI/multi-tool teams; Tessl for teams betting on bidirectional spec-code sync
3. **Spec quality**: Writing effective specs using Given/When/Then, domain language, explicit uncertainty markers
4. **Anti-drift practices**: Setting up CI/CD checks that validate code against specs; preventing spec drift
5. **Compounding insight**: SDD creates compounding value — each feature's spec becomes context for future features, reducing ambiguity over time

**Bryan Condor's entry point**: This repo already uses AGENTS.md as a lightweight spec/constitution (architectural rules, UI guidelines, security constraints). The natural progression is to adopt a formal SDD workflow for new feature development — starting with Spec-Kit CLI (works with Claude Code, no IDE switch required) or experimenting with Kiro for complex features.

**Warning to internalize** (Böckeler): "The discourse about AI-generated code review often feels binary. The answer is of course neither, because 'it depends.'" — SDD provides structure but judgment remains essential.
