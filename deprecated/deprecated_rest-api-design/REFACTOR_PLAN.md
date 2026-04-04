# REST API Design Page — Refactor Plan

**Source:** Three expert feedback reviews (engineering, copywriter, education)
**Target file:** `rest-api-design/index.html`
**Current size:** 2,391 lines

---

## 1. New Section Order

The page is restructured from academic order (theory → specs → practice) to **concrete-first** (use it immediately → understand why → go deeper).

### Before (current)
```
1.  Richardson Maturity Model     (#maturity)
2.  Foundational Theory & RFCs    (#foundations)
3.  Formal Specifications         (#specs)
4.  Industry Design Guides        (#industry)
5.  Real-World API Patterns       (#realworld)
6.  Versioning Strategies         (#versioning)
7.  Pagination Patterns           (#pagination)
8.  Error Handling                (#errors)
9.  Authentication Patterns       (#auth)
10. Rate Limiting                 (#ratelimit)
11. The N+1 Problem               (#n1)
12. Approach Comparison           (#comparison)
13. Full Benchmark                (#benchmark)
14. Books & Guides                (#books)
15. All Sources                   (#sources)
```

### After (proposed)
```
── FOUNDATION ──────────────────────────────────────────
1.  Intro & Prerequisites         (#intro)          ← NEW
2.  Richardson Maturity Model     (#maturity)       (keep as-is, it's the right opener)

── CORE PATTERNS ───────────────────────────────────────
3.  Error Handling                (#errors)         (moved up — first thing you hit)
4.  Pagination Patterns           (#pagination)     (moved up — needed for any list)
5.  Authentication Patterns       (#auth)           (moved up + expanded)
6.  Rate Limiting                 (#ratelimit)      (moved up)
7.  Versioning Strategies         (#versioning)     (moved up)
8.  The N+1 Problem               (#n1)             (moved up)

── PATTERNS IN THE WILD ────────────────────────────────
9.  Real-World API Patterns       (#realworld)      (moved — now reader has context)
10. Industry Design Guides        (#industry)       (restructured — consensus first)

── SYNTHESIS ───────────────────────────────────────────
11. Approach Comparison           (#comparison)     (keep)
12. Putting It Together           (#together)       ← NEW (worked orders API example)
13. Decision Scenarios            (#scenarios)      ← NEW (self-assessment)

── DEEP REFERENCE ──────────────────────────────────────
14. Foundational Theory & RFCs    (#foundations)    (moved to end — "go deeper")
15. Formal Specifications         (#specs)          (restructured — triage first)
16. Full Benchmark                (#benchmark)      (keep + add interpretations)
17. Books & Guides                (#books)          (keep + add reading path)
18. All Sources                   (#sources)        (keep)
```

---

## 2. New Sections to Add

### 2a. `#intro` — Who This Is For + What Is REST

**Purpose:** Prerequisites + minimal definition so beginners can calibrate.

```
Section label: Foundation
H2: Getting Started

Callout (prerequisites):
  This page assumes: HTTP methods (GET/POST/PUT/PATCH/DELETE), JSON, basic
  client-server architecture. Designed for developers who have built at least
  one API and want to understand the landscape of design approaches.

Subsection: "What is a REST API?"
  3-sentence definition: REST = architectural style, resources as nouns,
  stateless client-server communication over HTTP.

HTTP Methods table:
  | Method  | Purpose          | Safe | Idempotent |
  | GET     | Read             | Yes  | Yes        |
  | POST    | Create           | No   | No         |
  | PUT     | Replace          | No   | Yes        |
  | PATCH   | Partial update   | No   | No*        |
  | DELETE  | Delete           | No   | Yes        |

Callout (idempotency):
  Idempotent = calling it N times has the same effect as calling it once.
  Critical for retry safety. GET and DELETE are naturally idempotent; POST is not.
  PUT is idempotent because it replaces the full resource; PATCH is not by default.
```

### 2b. `#together` — Putting It Together (Worked Example)

**Purpose:** Show how versioning + pagination + errors + auth + N+1 compose in one real API.

```
Section label: Synthesis
H2: Putting It Together

Intro: "Here's a minimal but well-designed orders API applying the patterns
from this page. Each annotation links back to the relevant section."

Endpoint 1 — List orders with cursor pagination:
  GET /v1/orders?limit=25&starting_after=ord_abc123
  Stripe-Version: 2024-11-20
  Authorization: Bearer sk_live_...
  →
  200 OK
  {
    "data": [ { "id": "ord_xyz", "customer_id": "cus_123", ... } ],
    "has_more": true,
    "next_page_token": "ord_xyz"
  }
  [annotations: versioning header, cursor pagination, auth header]

Endpoint 2 — Get single order with expand:
  GET /v1/orders/ord_xyz?expand[]=customer
  →
  200 OK
  { "id": "ord_xyz", "customer": { "id": "cus_123", "email": "..." }, ... }
  [annotation: N+1 solution via expand]

Endpoint 3 — Create order (idempotency key):
  POST /v1/orders
  Idempotency-Key: client-uuid-here
  →
  201 Created
  Location: /v1/orders/ord_new
  [annotation: idempotency, 201 + Location]

Endpoint 4 — RFC 9457 error response:
  POST /v1/orders  (invalid payload)
  →
  422 Unprocessable Entity
  Content-Type: application/problem+json
  {
    "type": "https://api.example.com/errors/validation-failed",
    "title": "Validation Failed",
    "status": 422,
    "detail": "The 'quantity' field must be a positive integer.",
    "instance": "/logs/req-abc"
  }
  [annotation: RFC 9457 error format]
```

### 2c. `#scenarios` — Decision Scenarios (Self-Assessment)

**Purpose:** Retrieval practice — 4 realistic decisions the reader must work through.

```
Section label: Synthesis
H2: Decision Scenarios

Intro: "Four scenarios — each has a right answer based on the patterns
in this page. Work through them, then check the reasoning."

Scenario 1 — Pagination choice:
  "You're building a public API returning paginated product listings.
  The catalog has 800K items and changes frequently. Page 500 must load
  in < 100ms. Which pagination strategy?"
  → Answer: Cursor (keyset) — O(1) at any depth, consistent under writes.
    Offset would require OFFSET 12500 — full table scan.

Scenario 2 — Error format:
  "You're designing error responses for a new public API. Your users are
  developers integrating your service. Which error format?"
  → Answer: RFC 9457 Problem Details — machine-readable, standardized,
    extensible. Add doc_url (Stripe-style) for best DX.

Scenario 3 — Versioning strategy:
  "Your API has 10K active integrations. You need to rename a field
  (breaking change) without disrupting existing clients. Which approach?"
  → Answer: Date-based versioning (Stripe model) — each breaking change
    is a transform module. Old clients stay pinned; new clients opt in.

Scenario 4 — N+1 solution:
  "GET /orders returns 50 orders. Each order has a customer. You're seeing
  51 DB queries per request. Your clients are external developers with
  unpredictable access patterns. Fix it."
  → Answer: Add ?expand[]=customer opt-in embedding (Stripe pattern).
    Link by default; embed on demand. Don't embed eagerly because
    external clients have unknown needs.
```

---

## 3. Section Restructures (existing content, new structure)

### 3a. Industry Design Guides — consensus first

**Current:** 5 company entries (Google → Microsoft → Zalando → Atlassian → PayPal) → consensus callout at bottom

**New:**
```
1. Consensus callout (MOVED TO TOP):
   "Consensus across all 5 guides: Resource-oriented design with nouns
   (not verbs), standard HTTP methods mapped to CRUD, structured error
   responses, explicit versioning, and pagination as a first-class concern."

2. Divergence table (NEW):
   | Guide      | Naming (JSON) | Versioning          | Pagination        | Error format          | HATEOAS stance |
   | Google     | camelCase     | URL path /v1/        | Page token        | gRPC Status → HTTP    | Resource names |
   | Microsoft  | camelCase     | Header / query param | skip/top          | Custom ErrorResponse  | Not required   |
   | Zalando    | snake_case    | Avoid; media type    | Cursor (preferred)| RFC 9457 (MUST)       | L2 minimum     |
   | Atlassian  | camelCase     | URL path             | Offset + limit    | Custom JSON           | ?expand=       |
   | PayPal     | snake_case    | URL path             | Cursor + count    | Custom + HATEOAS      | Strong         |

3. Individual entries (existing, unchanged below the table)
```

### 3b. Formal Specifications — triage first

**Current:** 6 cards (JSON:API, HAL, OpenAPI, Protobuf, Siren, Collection+JSON) → "when to use" table at bottom

**New:**
```
1. Triage callout (NEW, at top):
   "For a typical REST API, you need two things:
   • OpenAPI — for documentation, code generation, and tooling (everyone needs this)
   • JSON:API — consider it if your API returns lists with repeated related objects
   The remaining formats (HAL, Siren, Collection+JSON) serve specific hypermedia
   use cases. Siren and Collection+JSON are niche — skip them unless you know you need them."

2. "When to use which" table (MOVED TO TOP, after triage callout)

3. Individual cards (existing, unchanged below the table)
```

### 3c. Authentication — add decision table

**Current:** 4 cards (API Keys, OAuth 2.0, JWT, Advanced) + callout

**New:** Add decision table before the cards:
```
| Situation                          | Mechanism          | Why                                      |
| Server-to-server, your own service | API Key            | Simple, no user context needed           |
| User-delegated access              | OAuth 2.0 Auth Code| Industry standard for delegated auth     |
| Machine-to-machine (third party)   | OAuth 2.0 Client Creds | Scoped, expirable, revokable         |
| Stateless, short-lived sessions    | JWT (Bearer)       | No DB lookup per request                 |
| Zero-trust, high security          | mTLS               | Cryptographic client identity            |
| Public SPA / mobile                | OAuth 2.0 + PKCE   | Secure for public clients without secret |
```

### 3d. N+1 — add terminology note

Add before the table:
```
Note: Different APIs use different names for the same core concept — including
related data inline to avoid extra requests. This table uses each API's native
terminology (expandable objects, compound documents, embed parameter) but they
all solve the same problem.
```

### 3e. RFC section — prioritize

Restructure the list:
```
Start here (daily use):
  • RFC 9110 — HTTP Semantics → authoritative HTTP reference
  • RFC 9457 — Problem Details → use for all error responses

Reference when needed:
  • RFC 8288 — Web Linking → reach for when building HATEOAS or Link header pagination
  • RFC 6585 — Additional Status Codes → defines 429 Too Many Requests
  • RFC 6902 — JSON Patch → reach for when you need fine-grained PATCH operations
  • RFC 7386 — JSON Merge Patch → simpler alternative to JSON Patch
  • RFC 6750 — Bearer Token → OAuth 2.0 token usage
```

### 3f. Books — add reading path callout

Add callout at top of section:
```
Where to start: Build APIs You Won't Hate (Sturgeon) if you're building your
first API — pragmatic and opinionated. Designing Web APIs (Jin et al.) if
you're thinking about API-as-product strategy. RESTful Web APIs (Richardson
et al.) for deep theory and hypermedia. Use the Cookbook and Rulebook as
ongoing references.
```

---

## 4. Content Rewrites (copywriter improvements)

| Location | Before | After |
|---|---|---|
| Header subtitle | "A curated benchmark of REST API design approaches..." | "How the best engineering teams design REST APIs — theory, standards, and real-world patterns from Stripe, GitHub, Google, and more. Every claim is sourced." |
| `#errors` section intro | "Structured, machine-readable errors are as important as correct responses. RFC 9457 is the emerging standard." | "A well-designed error is worth more than a well-designed success response — it's what your users see when they're stuck. RFC 9457 is becoming the industry standard for getting this right." |
| `#pagination` section intro | "How to page through large result sets — a choice with significant performance and consistency implications." | "Pagination seems simple until your dataset hits a million rows and your API grinds to a halt. The pattern you choose determines whether page 10,000 takes 5ms or 5 seconds." |
| `#ratelimit` section intro | "Standard headers, algorithms, and client-side strategies for fair API usage." | "Without rate limiting, one runaway script can take down your API for every user. Here's the standard toolkit — headers, algorithms, and the client-side patterns the biggest APIs rely on." |
| `#auth` section intro | "How clients prove identity — and how to choose the right mechanism." | "Every API needs auth — but the wrong choice creates either friction for legitimate users or exploitable holes. Here's how to choose." |
| `#benchmark` section intro | "Side-by-side scoring across five dimensions..." | "Everything on this page, scored and compared. Five dimensions — from theoretical design styles to real production APIs — rated by tooling, adoption, developer experience, and practical fit." |

---

## 5. Section Label Improvements (copywriter)

| Section | Current label | New label |
|---|---|---|
| `#versioning` | Pattern | The hardest decision |
| `#pagination` | Pattern | Performance at scale |
| `#errors` | Pattern | When things go wrong |
| `#n1` | Pattern | The silent killer |
| `#auth` | Pattern | Proving identity |
| `#ratelimit` | Pattern | Staying alive |
| `#together` | (new) | Synthesis |
| `#scenarios` | (new) | Synthesis |

---

## 6. Engineering Fixes

### 6a. Critical — ARIA tab system

**Current tab HTML (no ARIA):**
```html
<div class="tabs" role="tablist">
  <button class="tab-btn active" role="tab" data-tab="bm-styles">API Styles</button>
  ...
</div>
<div class="tab-panel active" id="bm-styles">...</div>
```

**New tab HTML (full ARIA):**
```html
<div class="tabs" role="tablist" aria-label="Benchmark categories">
  <button class="tab-btn active" role="tab" id="tab-bm-styles"
          aria-selected="true" aria-controls="bm-styles" data-tab="bm-styles">API Styles</button>
  <button class="tab-btn" role="tab" id="tab-bm-hypermedia"
          aria-selected="false" aria-controls="bm-hypermedia" tabindex="-1" data-tab="bm-hypermedia">Hypermedia Formats</button>
  <button class="tab-btn" role="tab" id="tab-bm-guides"
          aria-selected="false" aria-controls="bm-guides" tabindex="-1" data-tab="bm-guides">Industry Guides</button>
  <button class="tab-btn" role="tab" id="tab-bm-realworld"
          aria-selected="false" aria-controls="bm-realworld" tabindex="-1" data-tab="bm-realworld">Real-World APIs</button>
  <button class="tab-btn" role="tab" id="tab-bm-patterns"
          aria-selected="false" aria-controls="bm-patterns" tabindex="-1" data-tab="bm-patterns">Patterns</button>
</div>

<div class="tab-panel active" id="bm-styles" role="tabpanel" aria-labelledby="tab-bm-styles">...</div>
<div class="tab-panel" id="bm-hypermedia" role="tabpanel" aria-labelledby="tab-bm-hypermedia">...</div>
...
```

**New tab JS (ARIA + keyboard nav):**
```js
document.querySelectorAll('.tab-btn').forEach(function(btn) {
  btn.addEventListener('click', function() {
    var container = btn.closest('section');
    container.querySelectorAll('.tab-btn').forEach(function(t) {
      t.classList.remove('active');
      t.setAttribute('aria-selected', 'false');
      t.setAttribute('tabindex', '-1');
    });
    container.querySelectorAll('.tab-panel').forEach(function(p) {
      p.classList.remove('active');
    });
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

### 6b. High — Skip-to-content link

**Add immediately after `<body>` open:**
```html
<a href="#main-content" class="skip-link">Skip to content</a>
```

**Add `id="main-content"` to `<main>`:**
```html
<main id="main-content">
```

**CSS:**
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
  font-size: 13px;
}
.skip-link:focus {
  left: 16px;
  top: 16px;
}
```

### 6c. High — `:focus-visible` styles

**Add to global CSS (after universal reset):**
```css
:focus-visible {
  outline: 2px solid var(--accent);
  outline-offset: 2px;
}
```

### 6d. Medium — Score dots accessibility

**Add `.sr-only` CSS:**
```css
.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0,0,0,0);
  white-space: nowrap;
  border: 0;
}
```

**Add JS (after page load) to annotate score elements:**
```js
document.querySelectorAll('.score').forEach(function(el) {
  var dots = el.querySelectorAll('.dot');
  var total = 0;
  var filled = 0;
  dots.forEach(function(d) {
    var count = (d.textContent.match(/●/g) || []).length;
    filled += count;
    total += count;
  });
  var empties = el.querySelectorAll('.dot-off');
  empties.forEach(function(d) {
    total += (d.textContent.match(/●/g) || []).length;
  });
  el.setAttribute('role', 'img');
  el.setAttribute('aria-label', filled + ' out of ' + total);
});
```

### 6e. Medium — HTTP link fix

**Line 878 and line 2151:**
```
http://amundsen.com/  →  https://amundsen.com/
```

### 6f. Low — Inline styles → utility classes

**CSS to add:**
```css
.mt-xs  { margin-top: 4px; }
.mt-sm  { margin-top: 10px; }
.text-bold { font-weight: 600; color: var(--text); }
.callout-accent2 { border-left-color: var(--accent-2); }
.caption { font-size: 12px; color: var(--text-muted); margin-top: 8px; }
```

**HTML replacements:**
| Line | Before | After |
|------|--------|-------|
| 642 | `style="margin-top:12px;font-weight:600;color:var(--text);"` | `class="mt-sm text-bold"` |
| 651 | `style="margin-top:10px;"` | `class="mt-sm"` |
| 740 | `style="margin-top:10px;"` | `class="mt-sm"` |
| 897 | `style="margin-top:4px;"` | `class="mt-xs"` |
| 1588 | `style="border-left-color: var(--accent-2);"` | `class="callout callout-accent2"` |
| 1692 | `style="font-size:12px;color:var(--text-muted);margin-top:8px;"` | `class="caption"` |

### 6g. Low — CSS selector fix

**Line 150:**
```css
/* Before */
section:first-of-type { border-top: none; }

/* After */
main > section:first-of-type { border-top: none; }
```

### 6h. Low — Responsive / mobile improvements

**Tab touch target:**
```css
/* Before */
.tab-btn { padding: 10px 16px; }

/* After */
.tab-btn { padding: 12px 16px; }
```

**Add intermediate breakpoint at 768px:**
```css
@media (max-width: 768px) {
  .card-grid { grid-template-columns: repeat(auto-fill, minmax(240px, 1fr)); }
}
```

**Fix pattern-grid on very small screens (add to existing 600px block):**
```css
@media (max-width: 400px) {
  .pattern-grid { grid-template-columns: 1fr; }
}
```

---

## 7. TOC Restructure

Current TOC is a flat grid. New TOC adds group headings matching the page structure:

```html
<nav class="toc" aria-label="Page sections">
  <div class="toc-title">Contents</div>

  <div class="toc-group-label">Foundation</div>
  <ul class="toc-list">
    <li><a href="#intro">Getting Started</a></li>
    <li><a href="#maturity">Richardson Maturity Model</a></li>
  </ul>

  <div class="toc-group-label">Core Patterns</div>
  <ul class="toc-list">
    <li><a href="#errors">Error Handling</a></li>
    <li><a href="#pagination">Pagination Patterns</a></li>
    <li><a href="#auth">Authentication</a></li>
    <li><a href="#ratelimit">Rate Limiting</a></li>
    <li><a href="#versioning">Versioning Strategies</a></li>
    <li><a href="#n1">The N+1 Problem</a></li>
  </ul>

  <div class="toc-group-label">Patterns in the Wild</div>
  <ul class="toc-list">
    <li><a href="#realworld">Real-World API Patterns</a></li>
    <li><a href="#industry">Industry Design Guides</a></li>
  </ul>

  <div class="toc-group-label">Synthesis</div>
  <ul class="toc-list">
    <li><a href="#comparison">Approach Comparison</a></li>
    <li><a href="#together">Putting It Together</a></li>
    <li><a href="#scenarios">Decision Scenarios</a></li>
  </ul>

  <div class="toc-group-label">Deep Reference</div>
  <ul class="toc-list">
    <li><a href="#foundations">Foundational Theory & RFCs</a></li>
    <li><a href="#specs">Formal Specifications</a></li>
    <li><a href="#benchmark">Full Benchmark</a></li>
    <li><a href="#books">Books & Guides</a></li>
    <li><a href="#sources">All Sources</a></li>
  </ul>
</nav>
```

**CSS to add for group labels:**
```css
.toc-group-label {
  font-size: 10px;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.1em;
  color: var(--text-muted);
  margin: 14px 0 4px;
  opacity: 0.6;
}
.toc-group-label:first-of-type { margin-top: 0; }
```

---

## 8. Benchmark Tab Interpretation Paragraphs (education)

Add a 2-3 sentence paragraph below each tab panel:

**API Styles tab:**
> Level 2 (HTTP Verbs + Status Codes) dominates industry practice — Stripe, GitHub, and Twilio all operate here. The jump to Level 3 (HATEOAS) trades DX simplicity for theoretical evolvability that most teams never realize in practice. GraphQL's perfect DX score reflects its client-driven query model, which REST can approximate with expand and sparse fieldsets.

**Hypermedia Formats tab:**
> OpenAPI is the only format every API team needs — it's the contract for documentation, testing, and code generation. JSON:API has the broadest library support among hypermedia formats and shines for list APIs with repeated related objects. HAL, Siren, and Collection+JSON serve specific hypermedia use cases — most teams won't need them.

**Industry Guides tab:**
> The divergence between guides is smaller than it appears: naming convention and versioning strategy are the only meaningful splits. Zalando's RFC 9457 mandate and cursor-based pagination preference represent the most opinionated (and most principled) positions. Google's AIPs are the most comprehensive — they're worth reading even if you're not building Google-style APIs.

**Real-World APIs tab:**
> Stripe's perfect DX score reflects three investments: idempotency keys, expand parameters, and doc_url in every error response. The gap between Stripe and others is almost entirely in error handling and N+1 solutions — small design decisions that compound into dramatically different developer experiences. Shopify's move to GraphQL shows the natural ceiling of REST for complex data graphs.

**Patterns tab:**
> Date-based versioning is the gold standard specifically because it decouples change cadence from URL structure — Stripe has shipped 100+ breaking changes with zero disruption to pinned clients. Cursor pagination's O(1) performance at any depth is not just theoretical — it's the difference between a query that takes 5ms and one that takes 5 seconds at page 500. RFC 9457 is the only error format designed for interoperability — proprietary formats require clients to learn a new schema per API.

---

## 9. Implementation Sequence

When writing the new `index.html`, apply changes in this order:

1. **CSS block** — add skip-link, :focus-visible, .sr-only, utility classes, toc-group-label, touch target fix, breakpoints, selector fix
2. **`<body>` open** — add skip link `<a>`
3. **Header** — update subtitle
4. **TOC** — replace with grouped structure
5. **Sections in new order** — #intro (new), #maturity, #errors, #pagination, #auth (+ decision table), #ratelimit, #versioning, #n1 (+ terminology note), #realworld, #industry (restructured), #comparison, #together (new), #scenarios (new), #foundations (+ RFC prioritization), #specs (restructured), #benchmark (+ ARIA tabs + interpretations), #books (+ reading path), #sources
6. **`<main>` tag** — add `id="main-content"`
7. **JS block** — theme toggle (unchanged) + new ARIA tabs + score dots accessibility

---

## 10. What Does NOT Change

- All existing content (text, data, sources) — preserved verbatim unless listed above
- CSS design tokens (all 11 variables) — unchanged
- Theme toggle implementation — matches canonical AGENTS.md pattern exactly
- Page structure (header / main / footer / `.page-wrap`)
- All external links and source attribution
- `target="_blank" rel="noopener"` on all external links
- Back-to-home link
- Footer content
