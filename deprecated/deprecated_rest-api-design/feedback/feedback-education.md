# Education Expert Feedback — REST API Design Page

**Reviewer:** Education & Instructional Design Expert
**Date:** 2026-04-03
**Page:** `rest-api-design/index.html`

---

## Executive Summary

This page is an impressive, well-sourced reference on REST API design that succeeds as a **benchmark compendium** but underperforms as a **learning resource**. The content assumes significant prior knowledge (HTTP, JSON, databases, distributed systems) without acknowledging or scaffolding it. A reader who already understands REST will find this page tremendously valuable for comparing approaches; a reader trying to *learn* REST API design will hit a wall of terminology and comparison tables before building foundational mental models. The page excels at breadth and source attribution but lacks the progressive disclosure, worked examples, and conceptual scaffolding that turn reference material into education.

---

## What Works Well

- **Richardson Maturity Model as opener** — Starting with RMM is the correct pedagogical choice. It provides a framework the reader can use to orient everything that follows. The 4-level progression (Level 0 → 3) is naturally scaffolded.
- **Code examples in RMM section** — The appointment-booking examples across all 4 levels are excellent. Same domain, progressive complexity. This is textbook instructional design.
- **"Key insight" callouts** — The callout boxes (e.g., "Most production APIs operate at Level 2") give the reader permission to focus on what matters. These are the most educationally valuable elements on the page.
- **Source attribution on every claim** — Every statement links to its origin. This builds trust and gives learners a path to go deeper. Rare and valuable.
- **Consensus callouts** — The callout at the end of "Industry Design Guides" ("Consensus across all 5 guides: ...") synthesizes information across entries. This is exactly what learners need — someone to connect the dots.
- **"Why most production APIs don't implement HATEOAS"** — This subsection in the RMM section is outstanding. It anticipates the learner's question ("if Level 3 is the ideal, why isn't everyone doing it?") and answers it thoroughly.
- **Benchmark tabs** — The tabbed interface in the Full Benchmark section reduces cognitive overload by letting readers focus on one dimension at a time.
- **Decision framework table** (Approach Comparison section) — The "Situation → Recommendation" table is the single most actionable element for a practitioner. This is what turns knowledge into decisions.

---

## Issues Found

### 1. No explicit prerequisite statement or audience definition
**Problem:** The page never states who it's for or what background is assumed. Terms like "idempotent," "HATEOAS," "keyset pagination," "ETag," "OAuth 2.0 PKCE," and "FieldMask" appear without definition.
**Why it matters:** A beginner will bounce within 2 minutes. An intermediate reader won't know which sections to skip. There's no way to self-assess readiness.
**Suggested fix:** Add a brief "Who this is for" block after the header, stating: "This page assumes familiarity with HTTP methods, JSON, and basic client-server architecture. It's designed for developers who have built at least one API and want to understand the landscape of design approaches."
**Priority:** HIGH

### 2. Foundational Theory section is positioned too early and too dense
**Problem:** After the accessible RMM section, the reader hits Fielding's dissertation, 6 architectural constraints, 6 API rules, and 7 RFCs — all in one section. This is the densest part of the page and it comes second.
**Why it matters:** Cognitive load peaks immediately after the first section. The constraints table (Client-Server, Stateless, Cacheable, etc.) is abstract theory without concrete examples to anchor it. Most learners will disengage here and never reach the practical sections.
**Suggested fix:** Either (a) move Foundational Theory after Industry Guides + Real-World Patterns so readers encounter concrete examples before abstract theory, or (b) split the section — put the constraints table with brief examples early, and move the RFCs + Fielding's 6 rules into an "Advanced Theory" section near the end.
**Priority:** HIGH

### 3. RFCs are listed without contextual framing
**Problem:** The "Key RFCs" subsection lists RFC 9110, 9457, 8288, 6585, 6902, 7386, and 6750 as a bullet list with brief descriptions. No guidance on which ones a reader should actually read, in what order, or when they'd need them.
**Why it matters:** RFCs are intimidating. Dumping 7 of them with no prioritization signals "you need to read all of these" when in practice a developer needs RFC 9110 (HTTP semantics) and RFC 9457 (error format) for daily work, and the rest only situationally.
**Suggested fix:** Add a "Start here" annotation to RFC 9110 and RFC 9457. Group the others under "Reference when needed" with one-line use cases: "Reach for RFC 6902 when you need fine-grained PATCH operations."
**Priority:** MEDIUM

### 4. Formal Specifications section lacks a "when to care" framing
**Problem:** The section presents JSON:API, HAL, OpenAPI, Siren, Collection+JSON, and Protocol Buffers side-by-side as if a reader needs to evaluate all of them. The "when to use which" table at the bottom helps, but by the time the reader reaches it, they've already processed 6 dense cards.
**Why it matters:** For 90%+ of developers, only OpenAPI and *maybe* JSON:API are relevant. Presenting Siren and Collection+JSON with equal visual weight wastes attention on niche formats.
**Suggested fix:** Lead with a brief triage paragraph: "If you're building a typical REST API, you need OpenAPI (for documentation/tooling) and should consider JSON:API (for structured responses). The remaining formats — HAL, Siren, Collection+JSON — serve specific hypermedia use cases detailed below." Move the "when to use which" table to the TOP of the section.
**Priority:** MEDIUM

### 5. Industry Design Guides section is a passive catalog, not a learning experience
**Problem:** Five company guides are listed sequentially (Google, Microsoft, Zalando, Atlassian, PayPal) with bullet-point summaries. There's no synthesis until the consensus callout at the very end. The reader must mentally compare 5 entries to extract patterns.
**Why it matters:** Listing information is not teaching. The reader needs the page to do the comparative work for them — especially when the entries share 70%+ of their recommendations.
**Suggested fix:** Lead with the consensus callout (currently at the bottom). Then present a comparison table showing where the guides *differ* (naming conventions, versioning strategy, error format, HATEOAS stance). The individual guide entries can follow as expandable details or a secondary reference.
**Priority:** MEDIUM

### 6. No worked end-to-end example
**Problem:** Individual code snippets exist (RMM examples, cursor pagination SQL, RFC 9457 error response) but there's no cohesive example that ties multiple concepts together — e.g., "Here's what a well-designed order API looks like, applying versioning, pagination, error handling, and authentication."
**Why it matters:** Learners need to see how concepts compose. Without a unified example, each pattern feels isolated. The reader can't visualize a complete, well-designed API.
**Suggested fix:** Add a "Putting It Together" section before the Benchmark that shows a realistic mini-API (3-4 endpoints for an orders resource) demonstrating: URL structure, versioning header, paginated list response with cursor, an error response, and an expand parameter. Annotate each part with references back to the relevant section.
**Priority:** HIGH

### 7. Benchmark section is an information dump without interpretation
**Problem:** The Full Benchmark section contains 5 tabs of comparison tables with dot-score ratings (●●●○○) but no narrative interpretation. The reader sees that Stripe has 5/5 DX and WordPress has 3/5 — but the page doesn't explain *why* or what to learn from the difference.
**Why it matters:** Data without analysis is not education. The reader is left to draw their own conclusions from a dense grid, which most won't do. Benchmark tables work in academic papers because they're accompanied by a discussion section — this page has none.
**Suggested fix:** Add a 2-3 sentence interpretation paragraph below each tab. For "Real-World APIs": "Stripe's perfect DX score reflects their investment in idempotency keys, expand parameters, and doc_url in every error response. The gap between Stripe and others is primarily in error handling and N+1 solutions — areas where small design decisions compound into dramatically different developer experiences."
**Priority:** HIGH

### 8. No knowledge-check or self-assessment mechanism
**Problem:** After reading 2,000+ words of technical content, the reader has no way to verify their understanding. There are no questions, exercises, decision scenarios, or "test yourself" prompts.
**Why it matters:** Without retrieval practice, retention drops dramatically (the testing effect is one of the most robust findings in learning science). A reference page doesn't need quizzes, but a "learning page" does.
**Suggested fix:** Add a "Decision Scenarios" section with 3-5 realistic questions: "You're building a public API that returns paginated product listings. Products change frequently and the catalog has 500K items. Which pagination strategy should you choose and why?" Link each answer back to the relevant section.
**Priority:** MEDIUM

### 9. Books & Guides section lacks a reading path
**Problem:** Six books are presented as equivalent cards. No guidance on which to read first, which overlap, or which is most current.
**Why it matters:** A learner who wants to go deeper doesn't know where to start. The 2010 Cookbook and the 2018 "Designing Web APIs" serve very different needs, but this isn't surfaced.
**Suggested fix:** Add a brief recommendation: "Start with *Build APIs You Won't Hate* (pragmatic, opinionated) or *Designing Web APIs* (modern, case-study-driven). Move to *RESTful Web APIs* for deep theory. Use the *Cookbook* and *Rulebook* as ongoing references."
**Priority:** LOW

### 10. Authentication section is too shallow relative to its importance
**Problem:** Authentication gets 4 cards (API Keys, OAuth 2.0, JWT, Advanced Patterns) with bullet lists. No code examples, no flow diagrams, no decision framework for choosing between them. Meanwhile, hypermedia formats — a niche concern — get 6 detailed cards plus a comparison table.
**Why it matters:** Authentication is something every API developer must implement correctly. The current treatment is insufficient for someone to make an informed choice. The depth is inverted relative to practical importance.
**Suggested fix:** Add a decision table (like the ones in Versioning and Pagination) with columns: Use case, Mechanism, Complexity, Security level, When to choose. Add at least one code example showing a Bearer token in a request header and a 401 response.
**Priority:** MEDIUM

---

## Missing Content

1. **"What is a REST API?" preamble** — Even a 3-sentence definition at the top would anchor beginners. Currently the page assumes the reader already knows.
2. **URL/resource design section** — The page covers versioning, pagination, errors, auth, and N+1 but never addresses fundamental resource URL design: pluralization, nesting depth, naming conventions. These are referenced in Industry Guides but never taught as a standalone topic.
3. **Request/response lifecycle** — A visual or textual walkthrough of a complete API request: client sends request → server validates → processes → returns response with headers. This mental model is assumed but never established.
4. **PATCH vs PUT** — Referenced in passing (RMM Level 2, RFC 6902/7386) but never explained as a concept. When to use PATCH vs PUT is one of the most common REST design questions.
5. **Content negotiation** — Mentioned in the RFC 9110 description but never covered. How Accept/Content-Type headers work is fundamental.
6. **Caching in practice** — The Cacheable constraint is listed in the theory table, and ETag appears in the Microsoft section, but there's no practical coverage of Cache-Control headers, ETags, or conditional requests as a standalone topic.
7. **Putting It Together / Complete Example** — As noted in Issue #6, a worked example tying concepts together.
8. **Decision flowchart** — A simple "I'm designing an API, what decisions do I need to make and in what order?" visual would dramatically improve the page as a learning tool.
9. **GraphQL comparison** — GraphQL appears in the Benchmark table but is never discussed as a design alternative. Given that Shopify deprecated REST in favor of GraphQL, a brief "REST vs GraphQL: when to choose" section would be valuable.

---

## Proposed Learning Path

The current section order optimizes for **academic completeness** (theory → specs → industry → practice → patterns → benchmark). A learning-optimized order would be:

### Recommended restructured order:

1. **Intro / Who this is for** (NEW) — 3 sentences defining audience and prerequisites
2. **What is REST?** (NEW) — Brief definition, the client-server model, resources as nouns
3. **Richardson Maturity Model** (EXISTING, keep as-is) — The conceptual framework
4. **URL & Resource Design** (NEW) — Naming, pluralization, nesting, the basics
5. **Error Handling** (EXISTING) — Move up; errors are encountered immediately when building
6. **Pagination Patterns** (EXISTING) — Move up; needed for any list endpoint
7. **Authentication Patterns** (EXISTING, expanded) — Every API needs auth
8. **Versioning Strategies** (EXISTING) — Critical early decision
9. **The N+1 Problem** (EXISTING) — The most common performance pitfall
10. **Real-World API Patterns** (EXISTING) — Now the reader has context to appreciate these
11. **Industry Design Guides** (EXISTING, restructured) — Comparative, led by consensus
12. **Approach Comparison + Decision Framework** (EXISTING) — Synthesis
13. **Putting It Together** (NEW) — Worked end-to-end example
14. **Foundational Theory & RFCs** (EXISTING) — Now positioned as "go deeper" material
15. **Formal Specifications** (EXISTING) — Advanced reference
16. **Full Benchmark** (EXISTING, with interpretation) — Reference tables with analysis
17. **Books & Guides** (EXISTING, with reading path) — Next steps
18. **Decision Scenarios** (NEW) — Self-assessment
19. **All Sources** (EXISTING)

This order follows the **concrete → abstract** principle: start with what you can use immediately (resource design, errors, pagination), build to comparative analysis (industry patterns, real-world examples), then layer in theory (Fielding, RFCs, formal specs) for those who want depth.

---

## Priority Ranking

| # | Issue | Priority |
|---|-------|----------|
| 1 | No prerequisite / audience statement | HIGH |
| 2 | Foundational Theory too early and too dense | HIGH |
| 6 | No worked end-to-end example | HIGH |
| 7 | Benchmark has no interpretation | HIGH |
| 3 | RFCs listed without prioritization | MEDIUM |
| 4 | Formal Specifications lacks triage framing | MEDIUM |
| 5 | Industry Guides is a catalog, not synthesis | MEDIUM |
| 8 | No self-assessment / knowledge check | MEDIUM |
| 10 | Authentication section too shallow | MEDIUM |
| 9 | Books section lacks reading path | LOW |
