# Spec-Driven Development (SDD) Tools — Comprehensive Benchmark Report

> **Date:** March 18, 2026
> **Research scope:** 18 tools across the SDD ecosystem
> **Sources:** GitHub, Martin Fowler/Thoughtworks, Augment Code, Medium, official docs, TechCrunch

---

## What is Spec-Driven Development?

SDD inverts the traditional power structure: **specifications don't serve code — code serves specifications**. You define *what* to build in a structured spec, then AI agents generate the implementation. The spec remains the source of truth.

Martin Fowler's team identifies **three rigor levels**:

| Level | Description | Who uses it |
|---|---|---|
| **Spec-first** | Write spec before coding; code is the deliverable | Kiro, Taskmaster AI |
| **Spec-anchored** | Spec lives on after implementation for maintenance | Spec Kit, BMAD, OpenSpec |
| **Spec-as-source** | Spec IS the source of truth; humans never touch code | Tessl (aspiring) |

---

## The Big 3 (Industry Endorsed by Thoughtworks/Fowler)

### 1. GitHub Spec Kit

| Attribute | Value |
|---|---|
| **Maker** | GitHub (Microsoft) |
| **GitHub Stars** | ~71,000 ⭐ |
| **License** | MIT |
| **Spec format** | Markdown (constitution → spec → plan → tasks) |
| **Agent support** | 22+ agents (Claude Code, Copilot, Cursor, Gemini CLI, Windsurf, Codex…) |
| **Install** | `uvx --from git+https://github.com/github/spec-kit.git specify init <NAME>` |
| **Best for** | Teams wanting agent-agnostic, rigorous spec-first workflows |
| **SDD Level** | Spec-anchored |

**Workflow:** `Constitution → /specify → /plan → /tasks → /implement → /analyze → PR`

**Example spec (constitution.md):**
```markdown
# Project Constitution

## Core Principles
- All APIs must be RESTful and follow OpenAPI 3.1
- Authentication via JWT with refresh tokens
- Every endpoint must have integration tests
- No database queries in controllers — use repository pattern

## Tech Stack
- Backend: Node.js + TypeScript + Express
- Database: PostgreSQL with Prisma ORM
- Testing: Vitest + Supertest
```

**Example feature spec:**
```markdown
# Feature: User Registration

## What
New users can register with email/password and receive a verification email.

## Why
Required for user onboarding. Blocking feature for the mobile app launch.

## Acceptance Criteria
- Email must be unique and valid format
- Password: min 8 chars, 1 uppercase, 1 number
- Sends verification email via SendGrid
- Returns 201 with user object (no password hash)
- Returns 409 if email already exists

## Out of Scope
- Social login (OAuth) — separate feature
- Password reset flow
```

**Criticism:** "A lot of markdown files to review. Repetitive and very verbose." — [Scott Logic review](https://blog.scottlogic.com/2025/11/26/putting-spec-kit-through-its-paces-radical-idea-or-reinvented-waterfall.html)

🔗 [GitHub Repo](https://github.com/github/spec-kit) · [Official Site](https://speckit.org/) · [GitHub Blog](https://github.blog/ai-and-ml/generative-ai/spec-driven-development-with-ai-get-started-with-a-new-open-source-toolkit/)

---

### 2. Amazon Kiro

| Attribute | Value |
|---|---|
| **Maker** | AWS (Amazon) |
| **GitHub Stars** | N/A (proprietary IDE) |
| **License** | Proprietary (free tier: 50 interactions/month) |
| **Spec format** | Markdown with EARS notation (`.kiro/specs/`) |
| **Agent support** | Built-in (powered by Claude Sonnet) |
| **Platform** | VS Code fork (standalone IDE) |
| **Best for** | AWS-heavy teams wanting an integrated spec-driven IDE |
| **SDD Level** | Spec-first |

**Workflow:** `Natural language → Requirements (EARS) → Design doc → Task list → Implementation`

**Example spec (Kiro requirements):**
```markdown
# Feature: User Authentication

## Requirement 1: User Registration
### User Story
As a new user, I want to register with my email and password
so that I can access the platform.

### Acceptance Criteria (EARS notation)
- GIVEN a valid email and password
  WHEN the user submits the registration form
  THEN the system creates the account and sends a verification email
- GIVEN an email that already exists
  WHEN the user submits the registration form
  THEN the system returns a 409 Conflict error
```

**Key differentiator:** Agent Hooks (event-driven automation — e.g., on file save → run linter) and Agent Steering (persistent project context via `.kiro/steering/` markdown files).

**Criticism:** "Like using a sledgehammer to crack a nut" for small bug fixes. — [Martin Fowler article](https://martinfowler.com/articles/exploring-gen-ai/sdd-3-tools.html)

🔗 [Official Site](https://kiro.dev/) · [Kiro Docs: Specs](https://kiro.dev/docs/specs/) · [InfoQ Review](https://www.infoq.com/news/2025/08/aws-kiro-spec-driven-agent/)

---

### 3. Tessl Framework

| Attribute | Value |
|---|---|
| **Maker** | Tessl (founded by Guy Podjarny, ex-Snyk) |
| **GitHub Stars** | N/A (closed beta) |
| **Funding** | $125M (Index Ventures, Accel, GV, boldstart) |
| **License** | Proprietary / commercial |
| **Spec format** | YAML-based structured specs (1:1 mapping to code files) |
| **Agent support** | CLI + MCP server for multiple agents |
| **Best for** | Teams wanting spec-as-source (code is a generated artifact) |
| **SDD Level** | Spec-as-source (most ambitious) |

**How it works:** Reverse-engineers specs from existing code. Maintains a 1:1 mapping between spec files and code files. Generated code has `// GENERATED FROM SPEC - DO NOT EDIT` headers.

**Also offers:** Tessl Spec Registry — 10,000+ specs for open source libraries, preventing API hallucinations and version mixups.

**Example spec:**
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
    tests:
      - valid registration returns user without password_hash
      - duplicate email returns 409
      - invalid email format returns 400
```

🔗 [Official Site](https://tessl.io/) · [Tessl Blog](https://tessl.io/blog/tessl-launches-spec-driven-framework-and-registry/) · [Docs](https://docs.tessl.io/use/spec-driven-development-with-tessl)

---

## Rising Stars (High GitHub Stars, Fast Adoption)

### 4. Superpowers

| Attribute | Value |
|---|---|
| **Maker** | Jesse Vincent (obra) |
| **GitHub Stars** | ~88,400 ⭐ (fastest growing!) |
| **License** | Open source |
| **Approach** | Agentic skills framework + TDD enforcement |
| **Best for** | Solo devs / teams wanting strict TDD + spec-driven discipline |

**Key innovation:** Forces AI to brainstorm → plan → implement with hard gates. No implementation until design is approved. Enforces TDD — if code appears before tests, Superpowers deletes it.

**Subagent-driven development:** Dispatches fresh subagents for each task with two-stage review (spec compliance → code quality).

**Example (brainstorm skill):**
```markdown
## Brainstorm: User Registration Feature

### Questions to Explore
1. What authentication strategy? (JWT vs sessions vs OAuth2)
2. Email verification required before login?
3. Rate limiting on registration endpoint?
4. What happens to unverified accounts after 7 days?

### Proposed Design
[After Socratic questioning with developer...]
- JWT with refresh tokens (15min access / 7day refresh)
- Email verification required, 24h expiry
- Rate limit: 5 attempts per IP per hour
- Unverified accounts pruned via daily cron

### Approval Gate
⏸️ WAITING FOR HUMAN APPROVAL before proceeding to implementation
```

🔗 [GitHub Repo](https://github.com/obra/superpowers) · [Better Stack Guide](https://betterstack.com/community/guides/ai/superpowers-framework/)

---

### 5. BMAD-METHOD

| Attribute | Value |
|---|---|
| **Maker** | BMad Code (community) |
| **GitHub Stars** | ~19,100 ⭐ |
| **License** | Open source (100% free, no paywalls) |
| **Approach** | 21 specialized AI agents simulating an agile team |
| **Best for** | Enterprise teams wanting full SDLC simulation |

**Key innovation:** The most comprehensive SDD framework. 21 agents (Analyst, PM, Architect, Scrum Master, Dev, QA…), 50+ guided workflows, scale-adaptive intelligence.

**Two phases:**
1. **Agentic Planning** — Analyst + PM + Architect agents create PRDs and architecture docs
2. **Context-Engineered Development** — Scrum Master converts docs into hyper-detailed dev stories

**Example (BMAD agent flow):**
```
User Prompt → Analyst Agent (clarifies requirements)
            → PM Agent (writes PRD)
            → Architect Agent (creates architecture doc)
            → Scrum Master Agent (breaks into stories)
            → Developer Agent (implements per story)
            → QA Agent (validates against spec)
```

🔗 [GitHub Repo](https://github.com/bmad-code-org/BMAD-METHOD) · [Docs](https://docs.bmad-method.org/)

---

### 6. GSD (Get Stuff Done)

| Attribute | Value |
|---|---|
| **Maker** | Community (glittercowboy) |
| **GitHub Stars** | ~24,900 ⭐ |
| **License** | MIT |
| **Approach** | Context engineering + atomic task execution |
| **Best for** | Solo developers using Claude Code |

**Key innovation:** Each atomic task runs in a **fresh sub-agent** with a clean 200K token context window. Git is the memory layer.

**Three core documents:**
- **Project File** — high-level source of truth (the "what")
- **Roadmap** — phases and deliverables (the "how")
- **State Document** — tracks progress across sessions

**Example flow:**
```
Idea → Project File → Roadmap → Phase Plan →
  └─ Atomic Task 1 (fresh 200K context) → commit
  └─ Atomic Task 2 (fresh 200K context) → commit
  └─ Atomic Task 3 (fresh 200K context) → commit
→ Phase Complete → Next Phase
```

🔗 [GitHub Repo](https://github.com/glittercowboy/get-shit-done) · [Chase AI Blog](https://www.chaseai.io/blog/gsd-claude-code-solo-developer)

---

### 7. OpenSpec

| Attribute | Value |
|---|---|
| **Maker** | Fission AI |
| **GitHub Stars** | Growing (active community) |
| **License** | Open source |
| **Approach** | Brownfield-first, change isolation |
| **Best for** | Teams modifying existing codebases (brownfield) |

**Key innovation:** Two-folder model — `openspec/specs/` for current truth, `openspec/changes/` for proposed updates. Each change gets its own folder.

**Example workflow:**
```bash
# Propose a change
/opsx:propose add-dark-mode

# Creates:
# openspec/changes/add-dark-mode/
#   ├── proposal.md
#   ├── specs/
#   ├── design.md
#   └── tasks.md

# Implement
/opsx:apply

# Archive when done
/opsx:archive
```

🔗 [GitHub Repo](https://github.com/Fission-AI/OpenSpec) · [Official Site](https://openspec.dev/)

---

### 8. Augment Intent

| Attribute | Value |
|---|---|
| **Maker** | Augment Code |
| **License** | Proprietary (Standard $60/mo, Max $200/mo) |
| **Approach** | Multi-agent orchestration with living specs |
| **Best for** | Teams wanting an integrated SDD workspace with BYOA |

**Key innovation:** Three-agent architecture — Coordinator (plans), Specialists (6 personas execute in parallel), Verifier (validates against spec). Each workspace uses isolated git worktrees.

**Context Engine:** Processes 400,000+ files with semantic dependency analysis.

🔗 [Official Site](https://www.augmentcode.com/product/intent) · [Docs](https://docs.augmentcode.com/intent/overview)

---

### 9. Ralph Loop (Ralph Wiggum)

| Attribute | Value |
|---|---|
| **Creator** | Geoffrey Huntley |
| **Approach** | Autonomous loop: Read spec → pick task → implement → commit → restart |
| **Best for** | Autonomous overnight coding with spec guardrails |

**Key innovation:** Each iteration spawns a fresh agent process. Git is the memory layer. A developer shipped 100K LOC in 2 weeks with this approach.

**Loop cycle:**
```
Orient (read specs) → Pick Task → Implement & Test → Commit & Push →
DONE → [bash loop restarts with fresh context]
```

**Implementations:** smart-ralph, speckit-ralph, ralph-wiggum (supports Claude Code, Cursor, Codex, Windsurf, Amp, OpenCode)

🔗 [awesome-ralph](https://github.com/snwfdhmp/awesome-ralph) · [ralph-wiggum](https://github.com/fstandhartinger/ralph-wiggum)

---

### 10. Taskmaster AI

| Attribute | Value |
|---|---|
| **Maker** | Eyal Toledano |
| **GitHub Repo** | eyaltoledano/claude-task-master |
| **License** | Open source |
| **Approach** | PRD → Task decomposition → MCP-based execution |
| **Best for** | Cursor users wanting task-driven development |

**Install:** `npm install -g task-master-ai && task-master init`
**Workflow:** Parse PRD → Generate tasks → `task-master next` → implement

🔗 [GitHub Repo](https://github.com/eyaltoledano/claude-task-master)

---

### 11. Spec Kitty

| Attribute | Value |
|---|---|
| **Maker** | Priivacy AI |
| **License** | Open source |
| **Approach** | Kanban dashboard + git worktree isolation |
| **Best for** | Teams wanting visual SDD workflow with parallel feature branches |

**Key differentiator:** Only SDD tool with built-in worktree management and parallel feature isolation. Includes Kanban dashboard.

**Install:** `pip install spec-kitty-cli && spec-kitty init my-project --ai claude`

🔗 [GitHub Repo](https://github.com/Priivacy-ai/spec-kitty) · [Docs](https://priivacy-ai.github.io/spec-kitty/)

---

### 12. PromptX

| Attribute | Value |
|---|---|
| **Maker** | Deepractice |
| **Approach** | AI Agent Context Platform with role-based prompting |
| **Best for** | Teams wanting natural-language role assignment |
| **Academic** | Accepted at WWW Companion '26 |

**Key innovation:** 8 built-in specialist roles. "One sentence, one expert." Available as MCP server.

🔗 [GitHub Repo](https://github.com/Deepractice/PromptX)

---

### 13-15. Classic Spec-Driven Tools (API-First Era)

| Tool | Stars | Spec Format | Best For |
|---|---|---|---|
| **OpenAPI Generator** | ~23,000 ⭐ | OpenAPI YAML/JSON | API client/server codegen (50+ langs) |
| **AsyncAPI** | ~4,000+ ⭐ | AsyncAPI YAML | Event-driven API specs |
| **Buf (Protobuf)** | ~10,000+ ⭐ | Protocol Buffers | gRPC/Protobuf-first development |

**OpenAPI Generator example:**
```yaml
openapi: 3.0.3
info:
  title: User API
  version: 1.0.0
paths:
  /users:
    post:
      operationId: createUser
      requestBody:
        content:
          application/json:
            schema:
              type: object
              required: [email, password]
              properties:
                email: { type: string, format: email }
                password: { type: string, minLength: 8 }
      responses:
        '201':
          description: User created
```

```bash
# Generate TypeScript client
openapi-generator-cli generate -i spec.yaml -g typescript-axios -o ./client
```

🔗 [OpenAPI Generator](https://github.com/OpenAPITools/openapi-generator) · [AsyncAPI](https://www.asyncapi.com/) · [Buf](https://buf.build/)

---

### 16-18. Other Notable Tools

| Tool | Type | Key Differentiator |
|---|---|---|
| **Devika** (19.5K ⭐) | Autonomous AI engineer | Open-source Devin alternative; full agent loop |
| **Cucumber/Gherkin** | BDD framework | The OG spec-driven tool (Given/When/Then) |
| **Stoplight/Spectral** | API governance | Linting + mocking from OpenAPI specs |

---

## Master Comparison Table

| # | Tool | ⭐ Stars | SDD Level | Spec Format | Agent Lock-in | Best For | Cost |
|---|---|---|---|---|---|---|---|
| 1 | **Superpowers** | 88,400 | Spec-first + TDD | Markdown | None | Strict TDD discipline | Free |
| 2 | **Spec Kit** | 71,000 | Spec-anchored | Markdown | None (22+ agents) | Agent-agnostic teams | Free |
| 3 | **GSD** | 24,900 | Spec-first | Markdown | Claude Code primary | Solo devs | Free |
| 4 | **BMAD** | 19,100 | Spec-anchored | Markdown | None | Enterprise agile teams | Free |
| 5 | **Devika** | 19,500 | Autonomous | Natural language | None | Full autonomy | Free |
| 6 | **OpenAPI Gen** | 23,000 | API-first | OpenAPI YAML | None | API codegen (50+ langs) | Free |
| 7 | **Kiro** | N/A | Spec-first | Markdown (EARS) | AWS/Claude Sonnet | AWS-heavy teams | Free tier (50/mo) |
| 8 | **Tessl** | N/A | Spec-as-source | YAML | Multiple agents | Spec purists | Commercial |
| 9 | **Intent** | N/A | Spec-anchored | Living specs | BYOA | Enterprise multi-agent | $60-200/mo |
| 10 | **OpenSpec** | Growing | Spec-anchored | Markdown | None (20+ agents) | Brownfield codebases | Free |
| 11 | **Taskmaster** | Popular | Spec-first | PRD → tasks | Cursor primary | Cursor users | Free |
| 12 | **Spec Kitty** | Growing | Spec-anchored | Markdown | None | Parallel feature work | Free |
| 13 | **Ralph Loop** | Technique | Spec-first | Any spec format | None | Autonomous overnight runs | Free |
| 14 | **PromptX** | Growing | Role-based | Natural language | None (MCP) | Role-driven teams | Free |
| 15 | **BMAD + Ralph** | Combo | Spec-anchored | Markdown | None | Enterprise + autonomy | Free |
| 16 | **Buf** | 10,000+ | API-first | Protobuf | None | gRPC teams | Free tier |
| 17 | **AsyncAPI** | 4,000+ | API-first | AsyncAPI YAML | None | Event-driven APIs | Free |
| 18 | **Cucumber** | 5,000+ | BDD | Gherkin | None | QA-driven teams | Free |

---

## Decision Matrix: Which Tool For Your Use Case?

| If you are... | Use this |
|---|---|
| A **solo developer** wanting low friction | **GSD** or **Superpowers** |
| An **enterprise team** with agile processes | **BMAD-METHOD** |
| Building on **AWS** infrastructure | **Kiro** |
| Working on a **legacy/brownfield** codebase | **OpenSpec** |
| Wanting **agent-agnostic** spec workflows | **Spec Kit** |
| A **spec purist** (code = generated artifact) | **Tessl** |
| Needing **parallel feature development** | **Spec Kitty** |
| Using **Cursor** primarily | **Taskmaster AI** |
| Wanting **autonomous overnight coding** | **Ralph Loop** (+ any spec framework) |
| Building **APIs first** (REST/gRPC) | **OpenAPI Generator** or **Buf** |
| Wanting **multi-agent orchestration** | **Augment Intent** |
| Needing **strict TDD enforcement** | **Superpowers** |

---

## Spotify's Approach (Real-World Reference)

Spotify's top developers **haven't written code since December 2025** — they use Claude Code + their internal "Honk" system. Key enablers:

- **OpenAPI specs** for all public APIs (machine-readable contracts)
- **Backstage** (since 2020) — developer portal as central hub
- **Fleet Management** (since 2022) — automated code changes across hundreds of repos
- Engineers develop features **through Slack** — tell Claude to fix a bug, it deploys to staging

Result: 50+ new features shipped in 2025, premium subscribers up 10% YoY.

🔗 [TechCrunch: Spotify & AI](https://techcrunch.com/2026/02/12/spotify-says-its-best-developers-havent-written-a-line-of-code-since-december-thanks-to-ai/) · [Fast Company](https://www.fastcompany.com/91493217/spotify-ai-coding-new-features-claude)

---

## Key Takeaways

1. **The ecosystem exploded**: 170,000+ combined GitHub stars across the top 5 frameworks alone
2. **Spec Kit** is the most agent-agnostic and GitHub-native option
3. **Superpowers** has the most stars and enforces the strictest discipline (TDD)
4. **Kiro** is best if you're all-in on AWS
5. **Tessl** is the most ambitious (spec-as-source) but still in closed beta
6. **OpenSpec** is purpose-built for brownfield / existing codebases
7. **BMAD** offers the most comprehensive enterprise simulation
8. **Ralph Loop** is a technique, not a framework — combine it with any spec tool for autonomy
9. **Classic API-first tools** (OpenAPI, Buf, AsyncAPI) remain essential for contract-first API development

> "SDD is best suited to larger features and greenfield projects. Small bug fixes may not warrant the overhead." — [Martin Fowler / Thoughtworks](https://martinfowler.com/articles/exploring-gen-ai/sdd-3-tools.html)

---

## Sources

- [Martin Fowler: Understanding SDD — Kiro, spec-kit, and Tessl](https://martinfowler.com/articles/exploring-gen-ai/sdd-3-tools.html)
- [GitHub Blog: Spec-driven development with AI](https://github.blog/ai-and-ml/generative-ai/spec-driven-development-with-ai-get-started-with-a-new-open-source-toolkit/)
- [Augment Code: Best SDD Tools 2026](https://www.augmentcode.com/tools/best-spec-driven-development-tools)
- [Medium: SDD Is Eating Software Engineering (30+ frameworks)](https://medium.com/@visrow/spec-driven-development-is-eating-software-engineering-a-map-of-30-agentic-coding-frameworks-6ac0b5e2b484)
- [Medium: GSD vs Spec Kit vs OpenSpec vs Taskmaster AI](https://medium.com/@richardhightower/agentic-coding-gsd-vs-spec-kit-vs-openspec-vs-taskmaster-ai-where-sdd-tools-diverge-0414dcb97e46)
- [Medium: Superpowers vs BMAD vs SpecKit vs GSD](https://medium.com/@richardhightower/the-great-framework-showdown-superpowers-vs-bmad-vs-speckit-vs-gsd-360983101c10)
- [TechCrunch: Spotify AI Coding](https://techcrunch.com/2026/02/12/spotify-says-its-best-developers-havent-written-a-line-of-code-since-december-thanks-to-ai/)
- [SDD Comparison: BMAD vs spec-kit vs OpenSpec vs PromptX](https://redreamality.com/blog/-sddbmad-vs-spec-kit-vs-openspec-vs-promptx/)
- [spec-compare repo (6 tools compared)](https://github.com/cameronsjo/spec-compare)
