# Engineering Review — REST API Design Page

**Reviewer:** Software Engineer (frontend/code quality focus)
**File:** `rest-api-design/index.html`
**Lines reviewed:** 1–2391
**Date:** 2026-04-03

---

## Executive Summary

This is a well-structured, content-rich single-page learning resource built with clean, semantic HTML and a solid CSS variable system. The theme toggle follows the canonical repo pattern exactly. The page has strong fundamentals — proper use of `<header>`, `<main>`, `<nav>`, `<section>`, and `<footer>`, a consistent design token system, and working tab navigation. However, there are meaningful accessibility gaps (tab system lacks ARIA state management and keyboard support), a few CSS redundancies, one insecure HTTP link, and some mobile responsiveness issues with wide tables and the pattern grid. None of these are blocking, but several are high-priority for a public-facing page.

---

## What Works Well

- **Design token system is thorough** — 11 CSS variables covering all colors, including `--code-bg`, `--warning`, `--warning-bg`, and `--tag-bg` beyond the base set. No hardcoded colors found in any rule.
- **Theme implementation matches the canonical AGENTS.md pattern exactly** (lines 2348–2374) — stored > OS > dark fallback, `data-theme` on `<html>`, correct `localStorage` handling.
- **Semantic HTML structure** — proper `<header>`, `<main>`, `<nav aria-label="Page sections">`, `<section>` with IDs, `<footer>`. Document outline is logical and flat (no nesting issues).
- **Table of contents** uses a real `<nav>` element with `aria-label` (line 534).
- **Tables wrapped in `.table-wrap` with `overflow-x: auto`** (line 302–307) — correct pattern for horizontal scroll on mobile.
- **All external links have `target="_blank" rel="noopener"`** — verified across all ~80+ links. Security best practice followed consistently.
- **No inline event handlers** — all JS is in a single `<script>` block at the bottom.
- **CSS is logically grouped** with clear comment headers (Theme, Layout, Header, Nav, Section, Cards, Tables, Code, Callout, etc.).
- **Tab system scopes to the parent `<section>`** (line 2379) using `btn.closest('section')` — prevents interference if multiple tab groups exist.
- **Universal box-sizing reset** (line 38) — prevents layout bugs.
- **Font stack is system-first** (line 43) — no external font requests, zero render-blocking resources.

---

## Issues Found

### 1. Tab buttons lack ARIA state management and keyboard navigation
**Location:** Lines 1614–1619 (HTML), lines 2377–2386 (JS)
**Impact:** High — screen readers cannot determine which tab is selected; keyboard users cannot navigate between tabs with arrow keys.

The tab buttons have `role="tab"` but are missing:
- `aria-selected="true/false"` on each button
- `role="tablist"` on the container (currently just `class="tabs"`)
- `role="tabpanel"` and `aria-labelledby` on each panel
- `id` attributes on each tab button for `aria-labelledby` cross-references
- `tabindex` management (only active tab should be in tab order; arrow keys navigate between tabs)

**Suggested fix (HTML):**
```html
<div class="tabs" role="tablist" aria-label="Benchmark categories">
  <button class="tab-btn active" role="tab" id="tab-bm-styles"
          aria-selected="true" aria-controls="bm-styles" data-tab="bm-styles">API Styles</button>
  <button class="tab-btn" role="tab" id="tab-bm-hypermedia"
          aria-selected="false" aria-controls="bm-hypermedia" tabindex="-1" data-tab="bm-hypermedia">Hypermedia Formats</button>
  <!-- ... etc ... -->
</div>

<div class="tab-panel active" id="bm-styles" role="tabpanel" aria-labelledby="tab-bm-styles">
```

**Suggested fix (JS) — add arrow key navigation and aria-selected:**
```js
document.querySelectorAll('.tab-btn').forEach(function(btn) {
  btn.addEventListener('click', function() {
    var container = btn.closest('section');
    var tabs = container.querySelectorAll('.tab-btn');
    var panels = container.querySelectorAll('.tab-panel');
    tabs.forEach(function(t) {
      t.classList.remove('active');
      t.setAttribute('aria-selected', 'false');
      t.setAttribute('tabindex', '-1');
    });
    panels.forEach(function(p) { p.classList.remove('active'); });
    btn.classList.add('active');
    btn.setAttribute('aria-selected', 'true');
    btn.removeAttribute('tabindex');
    document.getElementById(btn.dataset.tab).classList.add('active');
  });

  btn.addEventListener('keydown', function(e) {
    var tabs = Array.from(btn.closest('[role="tablist"]').querySelectorAll('[role="tab"]'));
    var idx = tabs.indexOf(btn);
    var next;
    if (e.key === 'ArrowRight') next = tabs[(idx + 1) % tabs.length];
    else if (e.key === 'ArrowLeft') next = tabs[(idx - 1 + tabs.length) % tabs.length];
    else if (e.key === 'Home') next = tabs[0];
    else if (e.key === 'End') next = tabs[tabs.length - 1];
    if (next) { e.preventDefault(); next.click(); next.focus(); }
  });
});
```
**Priority:** Critical

---

### 2. No skip-to-content link
**Location:** Top of `<body>` (line 510–511)
**Impact:** Medium — keyboard users must tab through the theme toggle and entire navigation to reach content.

**Suggested fix:**
```html
<body>
  <a href="#main-content" class="skip-link">Skip to content</a>
  <button id="theme-toggle" ...>

<!-- Then on the main element: -->
<main id="main-content">
```
```css
.skip-link {
  position: absolute;
  left: -9999px;
  top: auto;
  z-index: 999;
  padding: 8px 16px;
  background: var(--accent);
  color: #fff;
  text-decoration: none;
  border-radius: 4px;
}
.skip-link:focus {
  left: 16px;
  top: 16px;
}
```
**Priority:** High

---

### 3. Focus styles are missing for interactive elements
**Location:** Global — no `:focus-visible` rules defined anywhere in the CSS
**Impact:** High — keyboard users have no visible focus indicator on links, buttons, or tab controls.

The browser default focus ring may be suppressed by the universal reset (`* { margin: 0; padding: 0; }`), and many browsers show minimal or invisible focus outlines on dark backgrounds.

**Suggested fix:**
```css
:focus-visible {
  outline: 2px solid var(--accent);
  outline-offset: 2px;
}
```
**Priority:** High

---

### 4. One insecure HTTP link (Collection+JSON)
**Location:** Line 878 and line 2151
**Impact:** Medium — mixed content warning possible; violates AGENTS.md security guidance ("All CDN scripts/stylesheets must use SRI — prefer inline code over CDN when possible"). While this is a link (not a resource), it's the only HTTP link on the page.

```html
<a ... href="http://amundsen.com/media-types/collection/format/">Collection+JSON spec ↗</a>
```

**Suggested fix:** Change to `https://amundsen.com/media-types/collection/format/` (the site does support HTTPS).
**Priority:** Medium

---

### 5. `section:first-of-type` selector is fragile
**Location:** Line 150 — `section:first-of-type { border-top: none; }`
**Impact:** Low — currently works because the first `<section>` inside `<main>` is the maturity section, but if a non-section element is inserted before it, or if sections are reordered, this could break unexpectedly.

**Suggested fix:** Use a class instead:
```css
.section-first { border-top: none; }
```
Or target more precisely: `main > section:first-of-type`
**Priority:** Low

---

### 6. Inline styles on several elements
**Location:** Lines 642, 651, 740, 897, 1588, 1692
**Impact:** Low — these `style="margin-top:12px"` and similar inline styles break the separation of concerns and make the CSS harder to maintain. They also increase specificity, making overrides harder.

Examples:
- Line 642: `<p style="margin-top:12px;font-weight:600;color:var(--text);">`
- Line 897: `<div class="entry-source" style="margin-top:4px;">`
- Line 1588: `<div class="callout" style="border-left-color: var(--accent-2);">`
- Line 1692: `<p style="font-size:12px;color:var(--text-muted);margin-top:8px;">`

**Suggested fix:** Create utility classes:
```css
.mt-sm { margin-top: 12px; }
.text-bold { font-weight: 600; color: var(--text); }
.callout-green { border-left-color: var(--accent-2); }
.caption { font-size: 12px; color: var(--text-muted); margin-top: 8px; }
```
**Priority:** Low

---

### 7. Duplicate CSS patterns for card-body and entry-body list styles
**Location:** Lines 216–229 (card-body lists) and lines 275–290 (entry-body lists)
**Impact:** Low — the two list styles are nearly identical but use different bullet characters (`·` vs `›`) and slightly different padding. This is intentional design but could be DRYer.

**Suggestion:** Extract a shared base and override only the differences:
```css
.card-body ul, .entry-body ul {
  list-style: none;
  padding: 0;
}
.card-body ul li, .entry-body ul li {
  position: relative;
  padding: 2px 0;
}
.card-body ul li { padding-left: 14px; }
.entry-body ul li { padding-left: 16px; }
.card-body ul li::before, .entry-body ul li::before {
  position: absolute;
  left: 0;
  color: var(--accent);
}
.card-body ul li::before { content: '·'; }
.entry-body ul li::before { content: '›'; font-weight: 700; }
```
**Priority:** Low

---

### 8. Theme toggle `localStorage.getItem` check in OS media query listener is redundant
**Location:** Lines 2366–2368
**Impact:** Negligible — the `mq.addEventListener('change', ...)` handler checks `if (!localStorage.getItem('theme'))` before applying, but `localStorage.setItem('theme', theme)` is called in `applyTheme()` on every page load (line 2363), so `localStorage.getItem('theme')` will always be truthy after initialization. This means the OS change listener is effectively dead code after first visit.

**Explanation:** On first visit with no stored theme, `applyTheme()` is called with the OS preference and immediately stores it — making the OS change handler a no-op afterward.

This matches the canonical AGENTS.md pattern exactly, so changing it would deviate from the repo standard. **Leave as-is** unless the canonical pattern is updated.
**Priority:** Informational only

---

### 9. Tab panel content is in the DOM but hidden with `display: none`
**Location:** Lines 488–489, all `.tab-panel` elements
**Impact:** Low — all tab panel content is rendered in the DOM at page load. For a page this size (~2400 lines), having all benchmark tables in the DOM is fine for performance. But if the page grows significantly, consider lazy rendering.

**Current behavior is acceptable.** Just noting for future reference.
**Priority:** Informational only

---

### 10. `<main>` element has no `id` attribute
**Location:** Line 531
**Impact:** Low — needed for skip link (see issue #2) and useful as a landmark target.

**Fix:** `<main id="main-content">`
**Priority:** Low (tied to issue #2)

---

## Accessibility Audit

### Passes
- `<html lang="en">` present (line 2)
- `<nav>` element with `aria-label="Page sections"` (line 534)
- Theme toggle has `aria-label="Toggle light/dark theme"` and `title` (line 512)
- Semantic landmarks: `<header>`, `<main>`, `<nav>`, `<section>`, `<footer>` all present
- `<table>` elements have `<thead>` with `<th>` headers
- Color is never the only indicator — pills have text labels alongside colors
- External links use `target="_blank" rel="noopener"`

### Fails
- **Tab system ARIA** — missing `aria-selected`, `role="tabpanel"`, `aria-labelledby`, `aria-controls`, and keyboard navigation (see issue #1) — **Critical**
- **No skip link** (see issue #2) — **High**
- **No visible focus indicators** (see issue #3) — **High**
- **Score dots (`●●●●●` / `●●●○○`) are purely visual** — screen readers will read "filled circle" characters without context. Consider adding a `<span class="sr-only">4 out of 5</span>` for each score, or use `aria-label` on the parent — **Medium**
- **`<pre>` code blocks have no accessible name** — long code blocks in screen readers are just walls of text with no indication of what they contain. Consider wrapping in `<figure>` with `<figcaption>` for the more significant examples — **Low**
- **Section IDs use terse names** (`#n1`, `#auth`, `#ratelimit`) — fine for URLs but `aria-label` on sections would improve screen reader navigation — **Low**

### Color Contrast
- **Dark theme:** `--text` (#e6edf3) on `--bg` (#0d1117) = 13.9:1 ratio (AAA pass)
- **Dark theme muted:** `--text-muted` (#7d8590) on `--bg` (#0d1117) = 4.7:1 (AA pass, AAA fail for small text)
- **Light theme:** `--text` (#1f2328) on `--bg` (#ffffff) = 16.6:1 (AAA pass)
- **Light theme muted:** `--text-muted` (#636c76) on `--bg` (#ffffff) = 5.3:1 (AA pass)
- **Pill colors on dark:** `--accent-2` (#3fb950) on `rgba(63,185,80,0.12)` background — effective contrast against dark `--bg` is adequate but tight; verify with real rendering.
- Overall: **AA compliant**, not fully AAA for muted text.

---

## Performance Notes

- **Zero external requests** — no fonts, no CDN scripts, no images. This is the best possible performance profile for a static page.
- **No render-blocking resources** — CSS is inline in `<style>`, JS is at the bottom of `<body>`.
- **Total HTML size:** ~2,400 lines / ~80KB — well within acceptable for a single-page resource. Browser rendering will be instantaneous.
- **`transition: background 0.2s, color 0.2s`** on `body` (line 47) — this is fine for theme switching but be aware it triggers a repaint on the root element. No performance concern at this page size.
- **`overflow-x: auto`** on `.table-wrap` — creates a stacking context per table, which is correct behavior.
- **All content in DOM on load** — the hidden tab panels add ~500 lines of DOM nodes that are parsed but not rendered. Negligible impact.
- **No lazy loading needed** — there are no images or heavy resources on the page.

**Verdict:** Excellent performance. Nothing to optimize.

---

## Mobile / Responsive Notes

### Current breakpoint: `@media (max-width: 600px)` (line 502)

**What works:**
- `.page-wrap` padding reduces from 40px to 20px
- `h1` drops from 26px to 20px
- `.card-grid` collapses to single column
- Tables have horizontal scroll via `.table-wrap`

**Issues:**

1. **Pattern grid stays at 2 columns on small screens** (line 506: `grid-template-columns: 1fr 1fr`) — at 320px viewport width, each column is only ~140px wide, which may be too narrow for the pattern card content. Consider `1fr` at `max-width: 400px`.

2. **Tab bar overflow** — `.tabs` has `overflow-x: auto` (line 467), which is correct, but the active tab indicator (`border-bottom: 2px`) may be clipped on very narrow screens. The 5 tab buttons ("API Styles", "Hypermedia Formats", "Industry Guides", "Real-World APIs", "Patterns") total ~400px+ and will require horizontal scrolling below ~420px. This is acceptable but the scrollbar may not be visible on mobile browsers — consider adding a scroll hint (gradient fade on the right edge).

3. **Wide benchmark tables** — the "Real-World APIs" tab has 8 columns which will definitely overflow on mobile. The `overflow-x: auto` handles this correctly, but users may not realize the table is scrollable. A subtle "scroll →" indicator would help.

4. **Touch targets** — tab buttons have `padding: 10px 16px` (line 478), giving ~35px touch height. The minimum recommended touch target is 44px (WCAG 2.5.8). Consider increasing to `padding: 12px 16px` minimum.

5. **No intermediate breakpoint** — the jump from 960px max-width to 600px is large. A breakpoint at ~768px could improve the tablet experience (e.g., 2-column card grids instead of auto-fill).

**Priority:** Medium overall — the page is usable on mobile but not optimized.

---

## Priority Summary

| # | Issue | Priority |
|---|-------|----------|
| 1 | Tab ARIA states + keyboard navigation | **Critical** |
| 2 | Skip-to-content link | **High** |
| 3 | Focus-visible styles | **High** |
| 4 | HTTP link (Collection+JSON) | **Medium** |
| 5 | Score dots need screen reader text | **Medium** |
| 6 | Mobile touch targets on tabs | **Medium** |
| 7 | Mobile scroll hints for wide tables | **Medium** |
| 8 | Inline styles → utility classes | **Low** |
| 9 | CSS DRY — card/entry list styles | **Low** |
| 10 | `section:first-of-type` fragility | **Low** |
| 11 | Add intermediate breakpoint (~768px) | **Low** |
| 12 | Pattern grid 2-col too narrow at 320px | **Low** |

---

*Review complete. The page is well-built with strong fundamentals. The critical path is accessibility: fix the tab ARIA, add skip link, add focus styles, and address score dot screen reader experience. Everything else is polish.*
