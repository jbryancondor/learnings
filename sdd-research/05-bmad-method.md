# 05 — BMAD-METHOD

## 1. Overview
The most comprehensive SDD framework — simulates an entire agile team with 21 specialized AI agents (Analyst, PM, Architect, Scrum Master, Developer, QA...) and 50+ guided workflows. Stands for "Build More Architect Dreams." Combines spec-driven development with "human-in-the-loop" governance and scale-adaptive intelligence.

## 2. Key Data

| Attribute | Value |
|---|---|
| **Maker** | BMad Code (community) |
| **Type** | Open-source agile AI framework |
| **GitHub Stars** | ~19,100 |
| **Forks** | 2,800+ |
| **License** | Open source (100% free, no paywalls, no gated content) |
| **Spec Format** | Markdown (PRDs + architecture docs + user stories) |
| **SDD Level** | Spec-anchored |
| **Agent Lock-in** | None (works with any AI assistant supporting custom prompts) |
| **Recommended Agent** | Claude Code |
| **Languages** | Language-agnostic |
| **Pricing** | Free |
| **Community** | Discord with 19K+ members |

## 3. How It Works

### Two Core Phases
1. **Agentic Planning** — Analyst, PM, and Architect agents collaborate with user to create:
   - Product Requirements Documents (PRDs)
   - Architecture designs
   - Technical specifications
2. **Context-Engineered Development** — Scrum Master agent converts planning docs into hyper-detailed dev stories with all context embedded.

### 21 Specialized Agents
Each agent is a well-defined persona with specific responsibilities. Key agents include:
- **Analyst** — Clarifies requirements and gathers context
- **PM** — Writes PRDs with acceptance criteria
- **Architect** — Creates system design and tech decisions
- **Scrum Master** — Converts docs into implementable stories
- **Developer** — Implements per story with embedded context
- **QA** — Validates against spec

### Scale-Adaptive Intelligence
Adjusts from bug fixes to enterprise systems — the workflow scales with problem complexity.

## 4. Example Spec

### Agent Flow
```
User Prompt: "Build a user registration system with email verification"

→ Analyst Agent:
  - What email provider? (SendGrid vs SES)
  - Password policy requirements?
  - Rate limiting needs?
  - Compliance requirements (GDPR)?

→ PM Agent (PRD):
  # User Registration System
  ## Business Requirements
  - Self-service registration to reduce support tickets by 40%
  - Email verification to prevent spam accounts
  ## User Stories
  - US-001: As a new user, I can register with email/password
  - US-002: As a new user, I receive a verification email
  - US-003: As a registered user, I can log in after verifying

→ Architect Agent:
  # Architecture Decision Record
  ## Auth Strategy: JWT with refresh tokens
  ## Email: SendGrid (transactional tier)
  ## Data Model:
  - users: id, email, password_hash, verified, created_at
  - verification_tokens: id, user_id, token, expires_at
  ## API Design:
  - POST /auth/register → 201 | 409
  - POST /auth/verify → 200 | 400
  - POST /auth/login → 200 (JWT) | 401

→ Scrum Master Agent:
  ## Story: US-001 — User Registration
  ### Context (embedded)
  - Auth: JWT per ADR-001
  - DB: PostgreSQL with Prisma (schema attached)
  - Email: SendGrid with templates
  ### Implementation Steps
  1. Create Prisma schema for users table
  2. Create POST /auth/register endpoint
  3. Hash password with bcrypt (12 rounds)
  4. Return 201 with user (exclude password_hash)
  ### Acceptance Criteria
  - [ ] Unique email constraint enforced
  - [ ] Password min 8 chars, 1 upper, 1 number
  - [ ] Returns 409 for duplicate email
```

## 5. Strengths
- Most comprehensive framework — 21 agents, 50+ workflows
- Simulates a full agile team (Analyst → PM → Architect → Dev → QA)
- Documentation becomes the source of truth (not just code)
- Scale-adaptive — adjusts complexity for bug fix vs. enterprise system
- 100% free, no paywalls, no gated Discord
- Agent-agnostic (works with any AI supporting custom prompts)
- Context engineering ensures every task gets full relevant context
- Active community (19K+ Discord members)

## 6. Weaknesses / Criticisms
- Learning curve — 21 agents and 50+ workflows can be overwhelming
- Heavy overhead for simple tasks
- More process-oriented than other tools (may feel like "process theater" for small teams)
- Requires significant setup and configuration
- Some critics note similarity to traditional waterfall with AI steps

## 7. Adoption & Community
- 19,100+ GitHub stars, 2,800+ forks
- Active Discord community with 19K+ members
- Featured in multiple comparison articles
- GMO Internet Group research blog (Japan) — enterprise adoption interest
- Academic interest — compared in formal SDD comparisons

## 8. When to Choose This Tool
- You're an **enterprise team** with existing agile processes
- You want a **full SDLC simulation** (not just coding)
- You need **multiple specialized agents** for different roles
- You value **comprehensive documentation** as source of truth
- You want the most **process-rich** framework available
- Your projects are **large-scale** with complex requirements

## 9. Sources
- [GitHub Repository](https://github.com/bmad-code-org/BMAD-METHOD)
- [Official Docs](https://docs.bmad-method.org/)
- [Medium: What is BMAD-METHOD?](https://medium.com/@visrow/what-is-bmad-method-a-simple-guide-to-the-future-of-ai-driven-development-412274f91419)
- [Medium: Comprehensive Guide — Kiro, Spec Kit, BMAD](https://medium.com/@visrow/comprehensive-guide-to-spec-driven-development-kiro-github-spec-kit-and-bmad-method-5d28ff61b9b1)
- [Redreamality: BMAD vs spec-kit vs OpenSpec vs PromptX](https://redreamality.com/blog/-sddbmad-vs-spec-kit-vs-openspec-vs-promptx/)
- [GMO Internet: BMAD Framework Review](https://recruit.group.gmo/engineer/jisedai/blog/the-bmad-method-a-framework-for-spec-oriented-ai-driven-development/)
- [Pasquale Pillitteri: SDD Frameworks Guide](https://pasqualepillitteri.it/en/news/158/framework-ai-spec-driven-development-guide-bmad-gsd-ralph-loop)
- [Medium: Superpowers vs BMAD vs SpecKit vs GSD](https://medium.com/@richardhightower/the-great-framework-showdown-superpowers-vs-bmad-vs-speckit-vs-gsd-360983101c10)
