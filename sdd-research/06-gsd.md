# 06 — GSD (Get Stuff Done)

## 1. Overview
A lightweight meta-prompting, context engineering, and spec-driven development system. Designed for solo developers using Claude Code. Key innovation: each atomic task runs in a fresh sub-agent with a clean 200K token context window. Git is the memory layer.

## 2. Key Data

| Attribute | Value |
|---|---|
| **Maker** | Community (glittercowboy) |
| **Type** | Open-source context engineering layer |
| **GitHub Stars** | ~24,900 |
| **License** | MIT |
| **Spec Format** | Markdown (Project File + Roadmap + State Document) |
| **SDD Level** | Spec-first |
| **Agent Lock-in** | Works with 20+ AI tools (Claude Code primary) |
| **Install** | Clone repo / integrate into project |
| **Languages** | Language-agnostic |
| **Pricing** | Free |

## 3. How It Works

### Core Architecture
Instead of one long chat session that degrades over time, GSD breaks your project into phases, sub-plans, and atomic tasks — executing each in a fresh sub-agent context.

### Three Core Documents
1. **Project File** — High-level source of truth. Lists core values, requirements, architecture. (The "what")
2. **Roadmap** — Tactical plan. Lists exact phases and deliverables. (The "how")
3. **State Document** — Tracks progress. When you start a new session, this tells the agent exactly where it left off.

### Execution Flow
```
Idea → Project File → Roadmap → Phase Plan →
  └─ Atomic Task 1 (fresh 200K context) → commit
  └─ Atomic Task 2 (fresh 200K context) → commit
  └─ Atomic Task 3 (fresh 200K context) → commit
→ Phase Complete → Next Phase
```

### Key Innovation
Every atomic task spins up a **fresh sub-agent** with a clean 200,000 token context window. This prevents context degradation that happens in long chat sessions.

## 4. Example Spec

### Project File
```markdown
# User Registration System

## Core Values
- Security first — bcrypt hashing, rate limiting, JWT tokens
- Simple UX — minimal form fields, clear error messages
- Testable — every endpoint has integration tests

## Key Requirements
- Email/password registration with verification
- JWT authentication (15min access, 7day refresh)
- Rate limiting (5 attempts/IP/hour)
- PostgreSQL + Prisma ORM

## Architecture
- Express.js REST API
- Repository pattern (no DB queries in controllers)
- SendGrid for transactional emails
```

### Roadmap
```markdown
# Roadmap

## Phase 1: Foundation (3 tasks)
- [ ] Database schema and migrations
- [ ] User model and repository
- [ ] Base Express app with error handling

## Phase 2: Auth (4 tasks)
- [ ] Registration endpoint + tests
- [ ] Email verification flow
- [ ] Login endpoint + JWT issuance
- [ ] Rate limiting middleware

## Phase 3: Polish (2 tasks)
- [ ] Input validation and error messages
- [ ] API documentation (OpenAPI)
```

### State Document (auto-updated)
```markdown
# Current State
## Phase: 2 (Auth)
## Last Completed: Registration endpoint + tests
## Next Task: Email verification flow
## Blockers: None
## Notes: SendGrid API key configured in .env
```

## 5. Strengths
- Fresh context per task — avoids context window degradation
- Git as memory layer — simple, reliable state management
- Low learning curve for solo developers
- Lightweight — no heavy framework overhead
- State document enables session persistence
- Works with 20+ AI tools
- MIT licensed

## 6. Weaknesses / Criticisms
- Primarily designed for solo developers (less suited for teams)
- Claude Code is the primary target (others are secondary)
- Less structured than BMAD or Spec Kit for enterprise use
- No built-in quality gates or review stages
- Spec-first only (not spec-anchored)

## 7. Adoption & Community
- 24,900+ GitHub stars
- Version 1.1.1 (January 2026)
- Featured in multiple "Get Stuff Done" AI framework articles
- Growing ecosystem of similar tools (Auto-Claude, Claude Cowork, etc.)

## 8. When to Choose This Tool
- You're a **solo developer** or small team
- You use **Claude Code** primarily
- You want **lightweight** SDD without heavy process
- Context window degradation is a real problem for you
- You want **atomic task execution** with fresh contexts
- You value **simplicity** over comprehensive process

## 9. Sources
- [GitHub Repository](https://github.com/glittercowboy/get-shit-done)
- [Chase AI: GSD for Solo Developers](https://www.chaseai.io/blog/gsd-claude-code-solo-developer)
- [Medium: GSD Meta-Prompting and SDD](https://agentnativedev.medium.com/get-sh-t-done-meta-prompting-and-spec-driven-development-for-claude-code-and-codex-d1cde082e103)
- [Medium: GSD vs Spec Kit vs OpenSpec vs Taskmaster AI](https://medium.com/@richardhightower/agentic-coding-gsd-vs-spec-kit-vs-openspec-vs-taskmaster-ai-where-sdd-tools-diverge-0414dcb97e46)
- [Pasquale Pillitteri: SDD Frameworks](https://pasqualepillitteri.it/en/news/158/framework-ai-spec-driven-development-guide-bmad-gsd-ralph-loop)
- [Vibe Sparking: SDD Frameworks](https://www.vibesparking.com/en/blog/ai/2026-01-25-spec-driven-development-frameworks-bmad-gsd-ralph/)
