# 03 — Tessl Framework

## 1. Overview
The most ambitious SDD tool — aspires to **spec-as-source** where code is a generated artifact and humans only edit specs. Founded by Guy Podjarny (creator of Snyk). Reverse-engineers specs from existing code and maintains 1:1 spec-to-code file mapping. Also offers a Spec Registry with 10,000+ open-source library specs.

## 2. Key Data

| Attribute | Value |
|---|---|
| **Maker** | Tessl (startup by Guy Podjarny, ex-Snyk founder) |
| **Type** | CLI + MCP server + Spec Registry |
| **GitHub Stars** | N/A (closed beta) |
| **Funding** | $125M (Index Ventures, Accel, GV, boldstart) |
| **License** | Proprietary / commercial |
| **Launched** | September 2025 (products) |
| **Spec Format** | YAML-based structured specs (1:1 mapping to code files) |
| **SDD Level** | Spec-as-source (most ambitious level) |
| **Agent Lock-in** | None — CLI works as MCP server for multiple agents |
| **Install** | CLI (similar to spec-kit) |
| **Languages** | Language-agnostic |
| **Pricing** | Commercial (details TBD) |

## 3. How It Works

### Two Products
1. **Tessl Framework** — Define what to build before coding. Specs live in the codebase as long-term memory, guiding agents as the app evolves.
2. **Tessl Spec Registry** — 10,000+ specs for open-source libraries. Prevents API hallucinations and version mixups.

### Workflow
1. Agent asks clarifying questions (not rushing to code)
2. Write specs first (or use "vibe-specs" — AI-generated)
3. Wait for human approval
4. Generate code from spec (code marked `// GENERATED FROM SPEC - DO NOT EDIT`)
5. Tests linked to spec capabilities enforce guardrails

### Key Innovation
Reverse-engineers specs from existing code. Maintains 1:1 mapping between spec files and code files. The spec is the artifact maintained by humans; code is derived.

## 4. Example Spec

```yaml
service: UserService
description: Manages user accounts and authentication

models:
  User:
    fields:
      - name: email
        type: string
        constraints: [unique, required, email_format]
      - name: password_hash
        type: string
        constraints: [required]
      - name: created_at
        type: datetime
        default: now()

capabilities:
  - name: register_user
    description: Register a new user account
    input: { email: string, password: string }
    output: User
    behavior:
      - validate email uniqueness
      - hash password with bcrypt
      - return created user without password_hash
    tests:
      - valid registration returns user without password_hash
      - duplicate email returns 409
      - invalid email format returns 400

api:
  - path: /users
    method: POST
    operation: register_user
    responses:
      201: User created
      409: Email already exists
      400: Validation error
```

## 5. Strengths
- Most ambitious SDD vision — true spec-as-source
- Spec Registry (10K+ specs) prevents AI hallucinations with libraries
- Founded by proven entrepreneur (Guy Podjarny built Snyk to unicorn)
- $125M funding — serious long-term investment
- Agent-agnostic via MCP server
- Reverse-engineers specs from existing code (brownfield capable)
- Specs pair with tests for enforcement

## 6. Weaknesses / Criticisms
- Still in closed beta — not generally available
- Proprietary and commercial (pricing unknown)
- 1:1 spec-to-code mapping may be too rigid for complex systems
- The spec-as-source vision is unproven at scale
- Martin Fowler's team notes similarity to Model-Driven Development (which never took off)
- Limited public adoption data

## 7. Adoption & Community
- Closed beta with design partners
- Backed by top-tier VCs (Index Ventures, Accel, GV)
- Featured in Martin Fowler's Thoughtworks article
- The Spec Registry addresses a real pain point (AI hallucinating APIs)
- IBM has adapted the SDD approach for infrastructure-as-code (inspired by Tessl)

## 8. When to Choose This Tool
- You want the **most ambitious SDD vision** (code as generated artifact)
- You have **existing codebases** that need specs reverse-engineered
- Your team struggles with **AI hallucinating library APIs** (Spec Registry solves this)
- You're willing to use a **commercial/proprietary** tool
- You want **spec-as-source** — humans maintain specs, not code
- You're in the **closed beta** program or willing to wait

## 9. Sources
- [Official Website](https://tessl.io/)
- [Tessl Blog: Launch Announcement](https://tessl.io/blog/tessl-launches-spec-driven-framework-and-registry/)
- [Tessl Blog: How Products Pioneer SDD](https://tessl.io/blog/how-tessls-products-pioneer-spec-driven-development/)
- [Tessl Docs: SDD with Tessl](https://docs.tessl.io/use/spec-driven-development-with-tessl)
- [Martin Fowler: Understanding SDD](https://martinfowler.com/articles/exploring-gen-ai/sdd-3-tools.html)
- [Calcalist: Guy Podjarny unveils Tessl's vision](https://www.calcalistech.com/ctechnews/article/i7ucn8teu)
- [Tessl Spec Registry](https://tessl.io/registry/tessl-labs/spec-driven-development/1.0.5)
- [DEV.to: SDD — Write the Spec, Not the Code](https://dev.to/bobbyblaine/spec-driven-development-write-the-spec-not-the-code-2p5o)
