# 01 — GitHub Spec Kit

## 1. Overview
GitHub's open-source toolkit for Spec-Driven Development (SDD). Provides a structured multi-step workflow: Constitution → Specify → Plan → Tasks → Implement → Analyze → PR. The most agent-agnostic SDD tool, supporting 22+ AI coding agents.

## 2. Key Data

| Attribute | Value |
|---|---|
| **Maker** | GitHub (Microsoft) |
| **Type** | Open-source CLI + slash commands |
| **GitHub Stars** | ~71,000 |
| **Forks** | 2,300+ |
| **License** | MIT |
| **Launched** | August 2025 |
| **Spec Format** | Markdown (constitution + specs + plans + tasks) |
| **SDD Level** | Spec-anchored |
| **Agent Lock-in** | None — 22+ agents supported |
| **Install** | `uvx --from git+https://github.com/github/spec-kit.git specify init <PROJECT>` |
| **Languages** | Language-agnostic |
| **Pricing** | Free |

## 3. How It Works

### Workflow
1. **Constitution** — `constitution.md` establishes non-negotiable project principles
2. **Specify** — `/specify`: provide high-level prompt, agent generates full spec
3. **Plan** — `/plan`: agent creates technical implementation plan
4. **Tasks** — Break plan into discrete, implementable tasks
5. **Implement** — `/speckit.implement` executes tasks
6. **Analyze** — `/analyze` acts as quality gate
7. **PR** — Create pull request

### Supported Agents
Claude Code, GitHub Copilot, Cursor, Gemini CLI, Windsurf, Codex CLI, Amp, Roo Code, Kilo Code, Qwen Code, OpenCode, Auggie CLI, and more.

## 4. Example Spec

### constitution.md
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

### Feature Spec (output of `/specify`)
```markdown
# Feature: User Registration

## What
New users can register with email/password and receive a verification email.

## Why
Required for user onboarding. Blocking feature for mobile app launch.

## Acceptance Criteria
- Email must be unique and valid format
- Password: min 8 chars, 1 uppercase, 1 number
- Sends verification email via SendGrid
- Returns 201 with user object (no password_hash)
- Returns 409 if email already exists

## Out of Scope
- Social login (OAuth) — separate feature
- Password reset flow
```

## 5. Strengths
- Agent-agnostic (works with 22+ agents — no vendor lock-in)
- Backed by GitHub/Microsoft (strong ecosystem integration)
- Constitution concept provides project-wide guardrails
- Quality gate via `/analyze` command
- Fastest-growing SDD tool (16K stars in first week)
- MIT licensed — fully free

## 6. Weaknesses / Criticisms
- "A lot of markdown files to review. Repetitive and very verbose" — Scott Logic
- "The workflow was slow, heavy, and less effective than iterative prompting" — Scott Logic
- Rigid phase gates feel heavyweight for small tasks
- Requires Python (`uvx`) for installation
- Not suitable for small bug fixes — overhead outweighs benefit

## 7. Adoption & Community
- 71,000+ GitHub stars (as of early 2026)
- Contributors from 50+ countries
- 110 releases through February 2026
- Endorsed by Microsoft Developer Blog
- Featured in Martin Fowler's Thoughtworks article on SDD

## 8. When to Choose This Tool
- You want **agent-agnostic** workflows (not locked to one IDE/agent)
- Your team uses **multiple AI coding tools** (Copilot, Claude Code, Cursor, etc.)
- You want a **rigorous, gated** spec process with quality checks
- You're working on **greenfield** or **medium-to-large** features
- You value **open source** and community-driven development

## 9. Sources
- [GitHub Repository](https://github.com/github/spec-kit)
- [Official Website](https://speckit.org/)
- [GitHub Blog: Spec-driven development with AI](https://github.blog/ai-and-ml/generative-ai/spec-driven-development-with-ai-get-started-with-a-new-open-source-toolkit/)
- [Microsoft Developer Blog](https://developer.microsoft.com/blog/spec-driven-development-spec-kit)
- [LogRocket: Exploring SDD with Spec Kit](https://blog.logrocket.com/github-spec-kit/)
- [Scott Logic: Putting Spec Kit Through Its Paces](https://blog.scottlogic.com/2025/11/26/putting-spec-kit-through-its-paces-radical-idea-or-reinvented-waterfall.html)
- [Martin Fowler: Understanding SDD](https://martinfowler.com/articles/exploring-gen-ai/sdd-3-tools.html)
- [IntuitionLabs Guide](https://intuitionlabs.ai/articles/spec-driven-development-spec-kit)
- [spec-driven.md specification](https://github.com/github/spec-kit/blob/main/spec-driven.md)
- [Mad Devs: SDD 0 to 1 with Spec-kit & Cursor](https://maddevs.io/writeups/project-creation-using-spec-kit-and-cursor/)
