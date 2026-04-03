## 0. Setup

- [ ] 0.1 Create `rest-api-design/` folder
- [ ] 0.2 Create `rest-api-design/index.html` as a new empty file (do not copy from deprecated)

---

> All tasks below are implemented in a single Write of the complete `rest-api-design/index.html`.
> Use `deprecated_rest-api-design/index.html` as a **content reference only** — not as a structural template.

---

## 1. HTML Shell

- [ ] 1.1 `<!DOCTYPE html>`, `<html lang="en">` with `data-theme` attribute (default: `"dark"`)
- [ ] 1.2 `<head>`: charset, viewport, `<title>REST API Design — Deep Dive</title>`
- [ ] 1.3 `<body>` first child: `<a href="#main-content" class="skip-link">Skip to content</a>`
- [ ] 1.4 `<header>`: page title, subtitle (rewritten), theme toggle button (`id="theme-toggle"`, `aria-label`)
- [ ] 1.5 `<main id="main-content">`: wraps all sections
- [ ] 1.6 Back-to-home link: `<a href="../home/">← Home</a>`

## 2. CSS

- [ ] 2.1 CSS custom properties — dark theme defaults on `:root` (`--bg`, `--bg-card`, `--border`, `--text`, `--text-muted`, `--accent`, `--accent-2`)
- [ ] 2.2 Light theme overrides on `[data-theme="light"]`
- [ ] 2.3 Global reset, box-sizing, font stack
- [ ] 2.4 `.sr-only` utility (clip-path screen-reader-only pattern)
- [ ] 2.5 `.skip-link` (position absolute, left -9999px, revealed on `:focus`)
- [ ] 2.6 `:focus-visible` global rule (`outline: 2px solid var(--accent); outline-offset: 2px`)
- [ ] 2.7 Utility classes: `.mt-xs`, `.mt-sm`, `.text-bold`, `.callout-accent2`, `.caption`
- [ ] 2.8 Layout: header, main, section, TOC grid, card grid, pattern grid
- [ ] 2.9 Tab system styles (`.tabs`, `.tab-btn`, `.tab-panel`)
- [ ] 2.10 Tab button padding: `12px 16px` (touch target)
- [ ] 2.11 `@media (max-width: 768px)` intermediate breakpoint
- [ ] 2.12 `@media (max-width: 400px)` — `.pattern-grid { grid-template-columns: 1fr }`
- [ ] 2.13 `main > section:first-of-type` selector (not `section:first-of-type`)

## 3. Grouped TOC

- [ ] 3.1 TOC with 5 named groups: **Foundation**, **Core Patterns**, **Patterns in the Wild**, **Synthesis**, **Deep Reference**
- [ ] 3.2 Foundation links: `#intro`, `#maturity`
- [ ] 3.3 Core Patterns links: `#errors`, `#pagination`, `#auth`, `#ratelimit`, `#versioning`, `#n1`
- [ ] 3.4 Patterns in the Wild links: `#realworld`, `#industry`
- [ ] 3.5 Synthesis links: `#comparison`, `#together`, `#scenarios`
- [ ] 3.6 Deep Reference links: `#foundations`, `#specs`, `#benchmark`, `#books`, `#sources`

## 4. Section — #intro (new)

- [ ] 4.1 `<section id="intro">` heading and intro paragraph
- [ ] 4.2 Prerequisites callout: HTTP methods, JSON, client/server model
- [ ] 4.3 "What is REST?" paragraph referencing Roy Fielding's dissertation
- [ ] 4.4 HTTP methods table: Method | Action | Safe | Idempotent
- [ ] 4.5 Idempotency definition callout with practical example

## 5. Section — #maturity

- [ ] 5.1 Port content from deprecated file (Richardson Maturity Model levels 0–3)
- [ ] 5.2 Verify all section content is complete and accurate

## 6. Section — #errors

- [ ] 6.1 Rewritten section intro ("a well-designed error is worth more than a well-designed success response")
- [ ] 6.2 Port all error handling content from deprecated file
- [ ] 6.3 Section label: "When things go wrong"

## 7. Section — #pagination

- [ ] 7.1 Rewritten section intro (stakes-based: million rows, 5ms vs. 5 seconds)
- [ ] 7.2 Port all pagination content from deprecated file
- [ ] 7.3 Section label: "Performance at scale"

## 8. Section — #auth

- [ ] 8.1 Rewritten section intro (stronger hook)
- [ ] 8.2 Decision table at top: Situation → Mechanism → Why
- [ ] 8.3 Port existing auth cards from deprecated file
- [ ] 8.4 Section label: "Proving identity"

## 9. Section — #ratelimit

- [ ] 9.1 Rewritten section intro (opens with concrete threat: runaway script)
- [ ] 9.2 Port all rate limiting content from deprecated file

## 10. Section — #versioning

- [ ] 10.1 Port all versioning content from deprecated file
- [ ] 10.2 Section label: "The hardest decision"

## 11. Section — #n1

- [ ] 11.1 Terminology note at top: expandable objects / compound documents / embed parameter = same core concept
- [ ] 11.2 Port all N+1 content from deprecated file
- [ ] 11.3 Section label: "The silent performance killer"

## 12. Section — #realworld

- [ ] 12.1 Port all real-world API content from deprecated file

## 13. Section — #industry

- [ ] 13.1 Consensus callout + divergence table at top of section
- [ ] 13.2 Individual guide entries follow below
- [ ] 13.3 Port all industry guide content from deprecated file

## 14. Section — #comparison

- [ ] 14.1 Port all comparison content from deprecated file

## 15. Section — #together (new)

- [ ] 15.1 `<section id="together">` heading and intro paragraph
- [ ] 15.2 Annotated code block: `GET /orders` — cursor pagination (links to `#pagination`)
- [ ] 15.3 Annotated code block: `GET /orders/:id?expand=line_items` — expand pattern (links to `#n1`)
- [ ] 15.4 Annotated code block: `POST /orders` with `Idempotency-Key` header (links to `#versioning`)
- [ ] 15.5 Annotated code block: RFC 9457 error response for validation failure (links to `#errors`)

## 16. Section — #scenarios (new)

- [ ] 16.1 `<section id="scenarios">` heading and intro paragraph
- [ ] 16.2 Scenario 1: Pagination style choice (feed API, 50M rows) — answer + reasoning
- [ ] 16.3 Scenario 2: Error format choice (public API, multiple clients) — answer + reasoning
- [ ] 16.4 Scenario 3: Versioning strategy (mobile app, long release cycles) — answer + reasoning
- [ ] 16.5 Scenario 4: N+1 solution (orders with line items, single-resource drilldown) — answer + reasoning

## 17. Section — #foundations

- [ ] 17.1 Port all foundations/constraints content from deprecated file

## 18. Section — #specs

- [ ] 18.1 Triage callout at top ("you need OpenAPI; JSON:API maybe; rest are niche") + decision table
- [ ] 18.2 Individual spec entries follow below
- [ ] 18.3 Port all formal specs content from deprecated file

## 19. Section — #benchmark

- [ ] 19.1 Rewritten section intro ("Everything on this page, scored and compared")
- [ ] 19.2 ARIA-compliant tab system (see task 20)
- [ ] 19.3 Port all benchmark tab content from deprecated file
- [ ] 19.4 Interpretation paragraph (2–3 sentences) below API Styles tab
- [ ] 19.5 Interpretation paragraph below Hypermedia Formats tab
- [ ] 19.6 Interpretation paragraph below Industry Guides tab
- [ ] 19.7 Interpretation paragraph below Real-World APIs tab
- [ ] 19.8 Interpretation paragraph below Patterns tab

## 20. ARIA Tab System

- [ ] 20.1 `role="tablist"` and `aria-label="Benchmark categories"` on `.tabs` container
- [ ] 20.2 Each tab button: `id`, `role="tab"`, `aria-selected`, `aria-controls`, `tabindex="-1"` on inactive tabs
- [ ] 20.3 Each tab panel: `role="tabpanel"`, `aria-labelledby`
- [ ] 20.4 Click handler: updates `aria-selected` and `tabindex` for all tabs on activation
- [ ] 20.5 Keydown handler: ArrowRight, ArrowLeft, Home, End — navigate and activate with `e.preventDefault()`

## 21. Section — #books

- [ ] 21.1 Reading path callout at top
- [ ] 21.2 Port all books content from deprecated file

## 22. Section — #sources

- [ ] 22.1 Port all sources content from deprecated file
- [ ] 22.2 All links must be `https://` — no `http://` links

## 23. JavaScript

- [ ] 23.1 Theme toggle (canonical monorepo pattern: localStorage → OS preference → dark default)
- [ ] 23.2 Tab system JS (click + keydown handlers, see task 20)
- [ ] 23.3 Score dot accessibility JS: scan `.score` elements, count `●`, set `role="img"` + `aria-label="X out of 5"`

## 24. Verification

- [ ] 24.1 Section order in DOM matches the 18-section concrete-first learning path
- [ ] 24.2 All TOC links navigate to correct sections
- [ ] 24.3 Tab keyboard nav: ArrowLeft/ArrowRight/Home/End work and wrap correctly
- [ ] 24.4 Skip link appears on focus and navigates to `#main-content`
- [ ] 24.5 `:focus-visible` ring visible on links, buttons, and tabs via keyboard
- [ ] 24.6 Score dots have `aria-label="X out of 5"` set correctly
- [ ] 24.7 No `http://` links in the file
- [ ] 24.8 No inline `style=""` attributes anywhere
- [ ] 24.9 Theme toggle works (dark/light) — `data-theme` switches on `<html>`
- [ ] 24.10 Mobile layout: tab touch targets, single-column pattern grid at 400px, 768px breakpoint
- [ ] 24.11 Back-to-home link present and points to `../home/`
