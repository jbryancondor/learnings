---
source: https://martinfowler.com/articles/exploring-gen-ai/to-vibe-or-not-vibe.html
date_accessed: 2026-04-04
published: 2025-09-23
author: Birgitta Böckeler
company: Thoughtworks
level_mapping: [1, 2, 3, 4]
tags: [vibe-coding, risk-assessment, ide, review-discipline, context-engineering, level-1, level-2, level-3, level-4]
agent: agent-3a
---

## Summary

"To Vibe or Not to Vibe" (Böckeler, September 2025) addresses the false binary in AI-assisted development discourse: either embrace "vibe coding" (generate without reviewing) or distrust all AI output. The article proposes a **risk assessment framework** as the principled middle path — the level of review should be proportional to the risk of failure, not uniformly applied.

This framework spans all four IDE/authoring levels: it applies whether you're accepting a tab completion (Level 1), running an agentic task (Level 2), evaluating context configurations (Level 3), or reviewing spec-generated code (Level 4).

## Key Concepts

### The False Binary

Most discourse presents two positions:
- **Vibe coding**: Accept all AI output without review; trust the model
- **Review everything**: Treat AI output as untrusted; line-by-line review always

Böckeler's argument: both extremes are wrong. The appropriate review intensity is situational.

### The Risk Assessment Framework

Three dimensions determine appropriate review level:

#### 1. Probability — How likely is AI to get things wrong?
- Tool quality and model capabilities (Claude Opus 4.6 vs smaller models)
- AI-friendliness of the tech stack (popular frameworks → better training data → lower error rate)
- Available context (does the agent have codebase access? good examples? search capability?)
- Codebase structure (clear, consistent patterns → better AI comprehension)

#### 2. Impact — What are the consequences if AI fails?
- Production vs spike/throwaway code
- Business criticality (payment flow vs internal tooling)
- Impact radius (shared library vs isolated component)
- Security sensitivity (auth code vs display logic)

#### 3. Detectability — Will errors be caught?
- Test coverage (well-tested code → errors caught before production)
- Typed languages (TypeScript catches class of errors; Python does not)
- System familiarity (you know the system → you'll notice anomalies)
- Change tracking reliability (git diff is clear → review is possible)

### The Sliding Scale

| Probability | Impact | Detectability | → Review Level |
|-------------|--------|---------------|----------------|
| Low | Low | High | Vibe OK — accept and move on |
| Low | High | High | Light review — scan for obvious issues |
| High | Low | High | Standard review — test it |
| High | High | Low | Thorough review — treat as untrusted PR |

### Application Across Levels 1–4

**Level 1 (Tab Complete)**:
- Low impact, high detectability → most tab completions can be accepted with quick glance
- Exception: completing security-sensitive code (auth, crypto, SQL) → requires careful review regardless of AI confidence

**Level 2 (Agentic IDE)**:
- Higher impact — agent touches multiple files, runs commands
- Review the diff as a whole; look for unintended file changes, scope creep
- Probability varies by task complexity; impact rises with change radius

**Level 3 (Context Engineering)**:
- Meta-level — errors in CLAUDE.md/AGENTS.md propagate to all future agent sessions
- High probability of subtle bugs (context files are hard to test)
- Low detectability without explicit testing of agent behavior
- → Always review context file changes carefully

**Level 4 (SDD / Compounding)**:
- Specs have high impact (they drive all implementation)
- Detectability can be high if specs include Given/When/Then tests
- SDD workflow is designed to make errors detectable earlier (spec review before code review)

### Partner-with-AI Pattern (Vaccari, July 2025)

From "Partner with AI and Throw Away the Code" (Matteo Vaccari, Thoughtworks):
- IDE tool used: **Cursor** with Claude Sonnet 4
- Core insight: Strategic partnership > blind automation
- Framework for decision:
  1. Ask AI to explain complex code (don't try to manually parse it)
  2. Generate unfamiliar utilities via AI (fill knowledge gaps)
  3. Improve test readability via AI-assisted refactoring
  4. Build understanding gradually via iterative prototypes
  5. **Restart from scratch when uncertain** — rewrite for clarity and correctness

> "I rewrote the core algorithm from scratch with my own hands, focusing on clarity." — Vaccari (demonstrating when human expertise must override AI)

**Result**: Performance improved from 7+ minutes to 0.57 seconds; memory reduced 74MB → 19MB

### Anchoring to Reference Applications (Böckeler, September 2025)

From "Anchoring to Reference":
- **Reference applications** serve as "golden paths" — compilable, consistent code samples for AI
- Technique: **few-shot prompting** — providing LLM with output examples improves results
- MCP server approach: expose git commits and code samples via MCP, enabling AI to detect "code pattern drift" between production codebases and reference implementations
- When AI excels over deterministic tools: complex, context-dependent transformations where regex-based codemods are insufficient

## Quotes / Evidence

> "The discourse about to what level AI-generated code should be reviewed often feels very binary... The answer is of course neither, because 'it depends.'" — Birgitta Böckeler, 2025

> "My initial idea for speeding up the operation was to use batch inserts and batch deletes." — Matteo Vaccari (demonstrating directive guidance beats expecting magic solutions)

> "Where AI can shine is whenever we have drift that needs coding that is more dynamic than is possible with regular-expression-based codemod recipes." — Böckeler, on AI vs deterministic tools

## Related Terms

- **Vibe coding** — AI-assisted coding where output is not reviewed; fast but risky
- **Risk-proportional review** — Böckeler's framework: review depth matches risk level
- **Pattern drift** — when production codebases diverge from reference/golden path implementations
- **Few-shot prompting** — providing examples in context; improves AI output quality
- **In-context learning** — model adapts behavior from examples without fine-tuning
- **Golden path** — reference implementation encoding organizational best practices
- **Codemod** — automated code transformation; deterministic alternative to AI for simple patterns

## Relevance to Generative AI Engineer Role

This cross-cutting perspective is critical for Bryan Condor's transition because it provides the **judgment framework** that governs all four levels:

1. **Tab complete** (Level 1): Fast acceptance is fine for low-risk completions; slow down for security code
2. **Agent IDE** (Level 2): Review agent diffs as PRs; scope matters more than line count
3. **Context files** (Level 3): Treat CLAUDE.md changes as high-stakes; test agent behavior after changes
4. **SDD** (Level 4): The spec is a risk multiplier — a wrong spec generates wrong code at scale; review specs before implementation begins

The key competency: **calibrated trust**. A Generative AI Engineer neither rubber-stamps AI output nor reviews it with paranoia. They apply judgment about probability, impact, and detectability to decide where to invest review effort.

This is also the framework that distinguishes a Generative AI Engineer from a vibe coder: not the tools used, but the judgment applied.
