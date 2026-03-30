# 04 — Superpowers

## 1. Overview
An agentic skills framework and software development methodology that enforces strict discipline on AI coding agents. The highest-starred SDD tool on GitHub. Forces brainstorm → plan → implement workflow with hard gates (no code until design is approved) and mandatory TDD (code before tests gets deleted).

## 2. Key Data

| Attribute | Value |
|---|---|
| **Maker** | Jesse Vincent (obra) |
| **Type** | Open-source agentic skills framework |
| **GitHub Stars** | ~88,400 |
| **License** | Open source |
| **Launched** | 2025 |
| **Spec Format** | Markdown (brainstorm → plan → tasks) |
| **SDD Level** | Spec-first + TDD enforcement |
| **Agent Lock-in** | None (works with Claude Code and others) |
| **Install** | Clone repo, add skills to agent |
| **Languages** | Language-agnostic |
| **Pricing** | Free |

## 3. How It Works

### Workflow
1. **Brainstorming** — Socratic questioning to refine ideas. Hard gate: no implementation until design approved.
2. **Planning** — Break approved designs into 2-5 minute tasks with exact file paths and code snippets.
3. **Subagent-Driven Development** — Dispatch fresh subagents per task with two-stage review.
4. **TDD Enforcement** — RED (failing test) → GREEN (minimal code) → REFACTOR. If code appears before tests, it gets deleted.

### Two-Stage Review
- **Stage 1:** Spec compliance review — "Does this match the specification?"
- **Stage 2:** Code quality review — "Is this clean and maintainable?"

### Key Philosophy
"Write tests first, always. Systematic over ad-hoc. Process over guessing. Simplicity as primary goal. Verify before declaring success."

## 4. Example Spec

### Brainstorm Output
```markdown
## Brainstorm: User Registration Feature

### Questions Explored (Socratic)
1. What authentication strategy? → JWT with refresh tokens (15min/7day)
2. Email verification required? → Yes, 24h expiry
3. Rate limiting? → 5 attempts per IP per hour
4. Unverified account cleanup? → Daily cron after 7 days

### Proposed Design
- JWT with refresh tokens (15min access / 7day refresh)
- Email verification required, 24h expiry
- Rate limit: 5 attempts per IP per hour
- Unverified accounts pruned via daily cron

### Approval Gate
⏸️ WAITING FOR HUMAN APPROVAL before proceeding to implementation
```

### Plan Output
```markdown
## Task 1: Create User model and migration (2 min)
- File: src/models/user.ts
- Migration: prisma/migrations/001_create_users.sql
- Fields: id (uuid), email (unique), password_hash, verified (bool), created_at
- Verification: Run migration, confirm table exists

## Task 2: Write registration endpoint test (3 min)
- File: tests/auth/register.test.ts
- Test cases: valid registration, duplicate email, weak password
- Must FAIL initially (RED phase)

## Task 3: Implement registration endpoint (5 min)
- File: src/routes/auth/register.ts
- Make tests pass (GREEN phase)
- REFACTOR for cleanliness
```

## 5. Strengths
- Highest GitHub stars of any SDD tool (~88K)
- Enforces real discipline — TDD is mandatory, not optional
- Hard gates prevent AI from rushing to code
- Subagent-driven development with fresh contexts per task
- Two-stage review catches both spec drift and code quality issues
- Socratic brainstorming produces better designs
- Treats AI implementer with healthy skepticism

## 6. Weaknesses / Criticisms
- TDD enforcement may be too strict for some teams
- Less structured than BMAD for enterprise SDLC
- No built-in spec persistence (more spec-first than spec-anchored)
- Learning curve for understanding the skills system
- Requires agent that supports skills/subagents well

## 7. Adoption & Community
- 88,400+ GitHub stars — fastest growing
- Gained 1,867 stars in a single day
- Active Hacker News community discussion
- Featured in Rick Hightower's "Great Framework Showdown" comparison
- Side-by-side comparisons show tangible quality improvements

## 8. When to Choose This Tool
- You want **strict TDD enforcement** (tests before code, always)
- You're a **solo developer** wanting disciplined AI assistance
- You value **quality over speed** (hard gates, two-stage review)
- You want **subagent-driven development** (fresh context per task)
- You believe in **Socratic brainstorming** before coding

## 9. Sources
- [GitHub Repository](https://github.com/obra/superpowers)
- [Hacker News Discussion](https://news.ycombinator.com/item?id=47341827)
- [Better Stack: Superpowers Guide](https://betterstack.com/community/guides/ai/superpowers-framework/)
- [Medium: Superpowers vs BMAD vs SpecKit vs GSD](https://medium.com/@richardhightower/the-great-framework-showdown-superpowers-vs-bmad-vs-speckit-vs-gsd-360983101c10)
- [ByteIota: 88.4K Stars](https://byteiota.com/superpowers-agentic-framework-27k-github-stars/)
- [DecisionCrafters: Superpowers Framework](https://www.decisioncrafters.com/superpowers-agentic-skills-framework/)
- [Ry Walker Research](https://rywalker.com/research/superpowers-skills-framework)
- [Spec Reviewer Prompt](https://github.com/obra/superpowers/blob/main/skills/subagent-driven-development/spec-reviewer-prompt.md)
