## Context

The original `rest-api-design/index.html` (2,391 lines, no build step, inline CSS/JS, GitHub Pages) has been archived as `deprecated_rest-api-design/`. A new `rest-api-design/index.html` will be built from scratch. The new file must follow all monorepo conventions: standalone HTML/CSS/JS, `data-theme` light/dark pattern, back-to-home link.

Three expert reviews (engineering, copywriter, education) produced 30+ improvements that inform the new design. The deprecated file serves as a content reference only — its structure and code are not carried forward.

**Why build from scratch instead of refactoring:**
- Section reorder touches ~2,000 lines — incremental edits carry high risk of ordering bugs
- Starting clean avoids carrying forward structural debt (inline styles, fragile selectors, incomplete ARIA)
- A fresh file can be designed with the correct learning path as its primary structure, not retrofitted

**Constraint:** Pure HTML/CSS/JS — no framework, no bundler. Single file output.

## Goals / Non-Goals

**Goals:**
- Build `rest-api-design/index.html` from scratch as an authoritative learning resource
- Concrete-first section order: Foundation → Core Patterns → Patterns in the Wild → Synthesis → Deep Reference
- Add `#intro`, `#together`, `#scenarios` sections
- WCAG AA compliance: tab system, focus management, score dots, skip link
- Grouped TOC with 5 named groups
- Zero inline styles (utility classes only)
- HTTPS links only
- Mobile-first responsive layout

**Non-Goals:**
- Modifying `deprecated_rest-api-design/` in any way
- Adding external dependencies (CDN, fonts, frameworks)
- Converting to a multi-page or component-based architecture
- Dynamic data fetching or server-side rendering

## Decisions

### D1 — Build from scratch vs. targeted edits

**Decision:** Write the complete new `rest-api-design/index.html` in a single operation.

**Rationale:** The section reorder alone requires repositioning ~2,000 lines. Starting from scratch is safer, produces a cleaner result, and guarantees no residual structure from the deprecated file carries over.

**Alternative considered:** Surgical edits on the deprecated file. Rejected — too many overlapping moves with no atomic guarantee; risk of residual structural debt.

### D2 — Section order

**Decision:** `#intro` → `#maturity` → `#errors` → `#pagination` → `#auth` → `#ratelimit` → `#versioning` → `#n1` → `#realworld` → `#industry` → `#comparison` → `#together` → `#scenarios` → `#foundations` → `#specs` → `#benchmark` → `#books` → `#sources`

**Rationale:** Concrete-first — developers can use errors and pagination immediately; Fielding's dissertation and formal specs are deep reference for those who want depth. Recommended by the education expert review.

**Alternative considered:** Keep original order, add `#intro` at top only. Rejected — the Foundational Theory section placed second causes cognitive overload before the reader reaches anything practical.

### D3 — ARIA tab implementation

**Decision:** WAI-ARIA Authoring Practices tabs pattern: `role="tablist"` on container, `role="tab"` + `aria-selected` + `aria-controls` + `id` on each button, `role="tabpanel"` + `aria-labelledby` on each panel, `tabindex="-1"` on inactive tabs, ArrowLeft/ArrowRight/Home/End keyboard navigation.

**Rationale:** Canonical accessible tab pattern matching screen reader expectations and engineering review spec.

**Alternative considered:** `<details>`/`<summary>` accordion. Rejected — visual tab design is correct; only ARIA attributes were missing.

### D4 — Score dot accessibility

**Decision:** Runtime JS scans all `.score` elements, counts `●` characters, sets `aria-label="X out of 5"` + `role="img"` on each.

**Rationale:** 25+ score cells across 5 benchmark tabs — manual annotation would be error-prone. JS approach is DRY and future-proof.

**Alternative considered:** Inline `<span class="sr-only">` in each score element. Rejected — volume of manual edits required.

### D5 — New sections content strategy

**Decision:** `#together` uses an orders API (list, get with expand, create with idempotency key, error response). `#scenarios` presents 4 closed-ended scenarios with revealed answers (no JS required).

**Rationale:** Orders API maps cleanly to all patterns covered in the page. Static scenario → answer pattern follows the "testing effect" without JS complexity.

### D6 — CSS architecture

**Decision:** All colors via CSS custom properties (`--bg`, `--bg-card`, `--border`, `--text`, `--text-muted`, `--accent`, `--accent-2`). Light/dark via `[data-theme="light"]` override on `<html>`. Zero inline `style=""` attributes — utility classes (`.mt-xs`, `.mt-sm`, `.text-bold`, `.callout-accent2`, `.caption`) for one-off overrides.

**Rationale:** Monorepo `data-theme` convention. Utility classes replace the inline styles from the deprecated file while keeping specificity predictable.

## Risks / Trade-offs

- **File size (~3,200 lines):** Remains zero-CDN, no external requests — parse time is negligible.
- **Content completeness:** All sections from the deprecated file must be preserved in the new build. The deprecated file serves as a content checklist.
- **Section IDs:** All `id` attributes must match the deprecated file's IDs exactly so that any existing bookmarks or TOC links remain valid.
- **ARIA keyboard nav:** ArrowLeft/ArrowRight/Home/End handlers must not intercept other keys or interfere with the click handler.

## Build Plan

1. Write complete new `rest-api-design/index.html` in one Write operation following the 18-section order
2. Verify in browser: section order, TOC links, tab ARIA + keyboard nav, skip link, focus indicators, theme toggle, mobile layout
3. Commit to `main` → GitHub Actions auto-deploys to Pages
4. `deprecated_rest-api-design/` remains in the repo as reference; no further action needed

## Open Questions

*(None — all decisions resolved.)*
