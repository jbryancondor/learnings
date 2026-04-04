# REST API Design — Reference Index

A curated index of authoritative sources used to evaluate and compare approaches for
designing REST APIs with good practices. Organized by topic.

---

## Foundational Models

| Source | URL | Key Concept |
|--------|-----|-------------|
| Richardson Maturity Model — Martin Fowler | https://martinfowler.com/articles/richardsonMaturityModel.html | The 4-level model (POX → Resources → HTTP Verbs → HATEOAS) |
| Richardson Maturity Model — Wikipedia | https://en.wikipedia.org/wiki/Richardson_Maturity_Model | Overview and critique of each level |
| REST APIs must be hypertext-driven — Roy Fielding | https://roy.gbiv.com/untangled/2008/rest-apis-must-be-hypertext-driven | Fielding's original clarification that HATEOAS is non-negotiable for true REST |

---

## Specifications & Standards

| Source | URL | Key Concept |
|--------|-----|-------------|
| JSON:API Specification (v1.1) | https://jsonapi.org/format/ | Compound documents, `relationships`, `included`, sparse fieldsets |
| JSON:API — Fetching Includes | https://jsonapi.org/format/#fetching-includes | `?include=` query parameter — opt-in compound documents |
| JSON:API — Sparse Fieldsets | https://jsonapi.org/format/#fetching-sparse-fieldsets | `?fields[type]=a,b` — per-type field filtering |
| HAL Specification | https://stateless.group/hal_specification.html | `_links` (references) and `_embedded` (opt-in inline data) |
| HAL vs HATEOAS — Baeldung | https://www.baeldung.com/java-hal-vs-hateoas | Comparison of HAL and generic HATEOAS approaches |

---

## Google API Design

| Source | URL | Key Concept |
|--------|-----|-------------|
| Google AIP-121: Resource-Oriented Design | https://google.aip.dev/121 | Hierarchical resources, parent-child collections |
| Google AIP-157: Partial Responses | https://google.aip.dev/157 | FieldMask (`?fields=`) for partial responses |
| Google Cloud Blog — Use Links Not Keys | https://cloud.google.com/blog/products/application-development/api-design-why-you-should-use-links-not-keys-to-represent-relationships-in-apis | Resource names as links instead of bare integer IDs |
| Google API Design Guide | https://cloud.google.com/apis/design | Full guide: naming, resource hierarchy, methods, errors |

---

## Real-World API Patterns

| Source | URL | Key Concept |
|--------|-----|-------------|
| Stripe — Expanding Responses | https://docs.stripe.com/expand | ID by default, opt-in expansion via `?expand[]=field` (dot-notation, max depth 4) |
| Stripe — API Reference | https://docs.stripe.com/api | Practical example of expandable object pattern at scale |
| GitHub REST API — Getting Started | https://docs.github.com/en/rest/using-the-rest-api/getting-started-with-the-rest-api | Eager embedding for always-needed relations; links for optional ones |
| WordPress REST API — Linking and Embedding | https://developer.wordpress.org/rest-api/using-the-rest-api/linking-and-embedding/ | `_links` + `?_embed` opt-in embedding in WordPress core |

---

## Pragmatic Best Practices

| Source | URL | Key Concept |
|--------|-----|-------------|
| Best Practices for a Pragmatic RESTful API — Vinay Sahni | https://www.vinaysahni.com/best-practices-for-a-pragmatic-restful-api | Opinionated, battle-tested decisions for real-world APIs |
| REST API Design — Resource Modeling — Thoughtworks | https://www.thoughtworks.com/insights/blog/rest-api-design-resource-modeling | How to model domain entities as REST resources |
| REST Embedding and Linking — Evert Pot | https://evertpot.com/rest-embedding-hal-http2/ | Trade-offs between embedding and linking; HTTP/2 implications |

---

## The N+1 Problem

| Source | URL | Key Concept |
|--------|-----|-------------|
| N+1 Problem in REST API Design — RESTful API Tutorial | https://restfulapi.net/rest-api-n-1-problem/ | How under-fetching causes N+1 round-trips and the solutions |
| JSON:API — Sparse Fieldsets — Aten Design Group | https://atendesigngroup.com/articles/json-api-getting-just-data-you-need-sparse-fieldsets | Practical walk-through of sparse fieldsets as an N+1 mitigation |

---

## Approach Comparison Summary

| Approach | Default for related resources | Opt-in embedding | Deduplication | Best for |
|----------|------------------------------|-----------------|---------------|----------|
| RMM Level 3 / HATEOAS | `_links` with `href` + `rel` | No standard | N/A | True REST compliance |
| JSON:API | `relationships` (type + id) | `?include=relation` | Yes — single `included` array | APIs with repeated related objects in lists |
| HAL | `_links` | `_embedded` (server-controlled) | No | Hypermedia-first APIs |
| Google AIP | Resource name (full URL path) | FieldMask (`?fields=`) | N/A | Large, multi-team public APIs |
| Stripe | Bare ID string | `?expand[]=field` (dot-notation) | No — duplicated inline | Developer-facing APIs with flexible clients |
| GitHub | Eager embed for frequent, link for rare | No standard mechanism | N/A | Known clients with stable access patterns |

---

## Decision Framework

> **Link by default. Embed by exception, driven by measured client usage.**

| Situation | Recommendation |
|-----------|---------------|
| Related resource is always needed with the parent | Embed by default (GitHub `owner` inside `repository`) |
| Related resource is sometimes needed | Link by default + `?expand=` on demand (Stripe) |
| Same related object repeated across a large list | `?include=` with deduplication (JSON:API) |
| Unknown external clients | Link by default; let clients opt in |
| Internal API with known, uniform clients | Embed what is always needed; skip expansion infrastructure |
| Need partial fields from related objects | Sparse fieldsets (`?fields[type]=a,b`) or FieldMask |
| Deep nested relationship traversal needed | Stripe dot-notation (`invoice.subscription.payment_method`) with depth limit |
