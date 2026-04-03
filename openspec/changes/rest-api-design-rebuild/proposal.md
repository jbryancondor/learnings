## Why

The original `rest-api-design/index.html` was a well-sourced reference compendium but underperformed as a learning resource. Three expert reviews (engineering, copywriter, education) surfaced 30+ concrete improvements. Rather than patching the existing file, the decision was made to:

1. Archive the existing page as `deprecated_rest-api-design/` (preserved for reference)
2. Build a fresh `rest-api-design/index.html` from scratch, incorporating all improvements by design — not as an afterthought

Building from scratch avoids residual structure from the old file, produces a cleaner result, and allows the new page to be designed with the correct learning path from the ground up.

## What Changes

- **New file:** `rest-api-design/index.html` — built from scratch, replacing the deprecated version
- **Deprecated:** `deprecated_rest-api-design/index.html` — preserved as-is, not modified

### New sections
- **`#intro`** — prerequisites callout + "What is REST?" + HTTP methods table with Safe/Idempotent columns + idempotency callout
- **`#together`** — worked end-to-end orders API example (list with cursor pagination, get with expand, create with idempotency key, RFC 9457 error)
- **`#scenarios`** — 4 decision scenarios with answers and reasoning (pagination choice, error format, versioning strategy, N+1 solution)

### Architecture
- **Concrete-first section order:** Foundation → Core Patterns → Patterns in the Wild → Synthesis → Deep Reference (18 sections)
- **Grouped TOC:** 5 named groups matching the learning path
- **ARIA-compliant tab system:** `role="tablist"`, `aria-selected`, `role="tabpanel"`, `aria-labelledby`, `aria-controls`, keyboard nav (ArrowLeft/ArrowRight/Home/End)
- **Accessibility baseline:** skip link, `:focus-visible` global rule, `.sr-only` utility, score dot `aria-label` via JS
- **Zero inline styles:** all styling via CSS custom properties and utility classes
- **HTTPS only:** no `http://` links anywhere in the file
- **Mobile-first responsive:** tab touch targets (12px padding), 768px and 400px breakpoints

### Section improvements (carried over from expert reviews)
- Industry Guides: consensus callout + divergence table at top
- Formal Specs: triage callout + decision table at top
- Auth: decision table (Situation → Mechanism → Why) before cards
- N+1: terminology note (expandable objects / compound documents / embed = same concept)
- RFC: split into "Start here" vs. "Reference when needed"
- Books: reading path callout at top
- Benchmark tabs: 2–3 sentence interpretation paragraph below each tab

### Content rewrites
- Page subtitle
- 5 section intros (pagination, errors, rate limiting, auth, benchmark)
- 7 section labels (e.g. Versioning → "The hardest decision")

## Capabilities

### New Capabilities

- `page-intro-section`: Prerequisites callout, REST definition, HTTP methods table with Safe/Idempotent columns, idempotency callout
- `page-together-section`: Worked orders API example across 4 annotated endpoints
- `page-scenarios-section`: Four decision scenarios with answers and reasoning
- `page-aria-tabs`: Full ARIA-compliant tab system with keyboard navigation
- `page-accessibility-baseline`: Skip link, `:focus-visible` styles, `.sr-only` utility, score dot `aria-label` annotations

### Modified Capabilities

*(None — this is a fresh build. No delta against prior specs.)*

## Impact

- **File created:** `rest-api-design/index.html` (new file, ~3,200 lines estimated)
- **File preserved:** `deprecated_rest-api-design/index.html` (untouched)
- **No build step** — pure HTML/CSS/JS, deployed automatically to GitHub Pages on push to `main`
- **No breaking changes to other pages** — standalone page, no shared components
- **Accessibility:** WCAG AA compliant tab system, full keyboard navigation
- **No external dependencies** — zero-CDN, zero-external-request
- **home/index.html** — card already points to `rest-api-design/`; no change needed there
