# 07 — OpenSpec

## 1. Overview
A lightweight spec-driven framework built for **brownfield** (existing codebases). Key innovation: two-folder model separating current specs from proposed changes, with each change isolated in its own folder. Designed by Fission AI. Requires no API keys, no MCP — just Node.js.

## 2. Key Data

| Attribute | Value |
|---|---|
| **Maker** | Fission AI |
| **Type** | Open-source CLI framework |
| **GitHub Stars** | Growing (active community) |
| **License** | Open source |
| **Spec Format** | Markdown (proposals + specs + design + tasks) |
| **SDD Level** | Spec-anchored |
| **Agent Lock-in** | None (20+ agents: Claude Code, Cursor, Codex, Copilot, Gemini CLI…) |
| **Install** | `npm install -g @fission-ai/openspec@latest` |
| **Requirements** | Node.js 20.19.0+ |
| **Languages** | Language-agnostic |
| **Pricing** | Free |

## 3. How It Works

### Two-Folder Model
- `openspec/specs/` — Current truth (the state of the system)
- `openspec/changes/` — Proposed updates (each change in its own folder)

This separation keeps state and diffs separate — scales when you modify existing features or touch multiple specs.

### Workflow
1. **Propose** — `/opsx:propose add-dark-mode`
   - Creates: `openspec/changes/add-dark-mode/`
     - `proposal.md` — What and why
     - `specs/` — Affected specifications
     - `design.md` — Technical approach
     - `tasks.md` — Implementation steps
2. **Apply** — `/opsx:apply` — Agent implements tasks one by one
3. **Archive** — `/opsx:archive` — Change is archived, specs updated

### Key Innovation
**Brownfield-first strategy** — unlike tools focused on greenfield (0→1), OpenSpec is designed for existing codebase evolution (1→n). Change isolation prevents one change from interfering with another.

## 4. Example Spec

### Proposing a Change
```bash
/opsx:propose add-user-registration
```

### Generated Structure
```
openspec/changes/add-user-registration/
├── proposal.md
├── specs/
│   ├── user-model.md
│   └── auth-endpoints.md
├── design.md
└── tasks.md
```

### proposal.md
```markdown
# Proposal: User Registration

## What
Add email/password registration with verification flow.

## Why
Required for user onboarding. Currently no self-service account creation.

## Impact
- New: User model, auth endpoints, email service integration
- Modified: Database schema (new users table)
- Dependencies: SendGrid for email delivery
```

### specs/auth-endpoints.md
```markdown
# Auth Endpoints Spec

## POST /auth/register
- Input: { email: string, password: string }
- Validates email format and uniqueness
- Password: min 8 chars, 1 upper, 1 number
- Hashes password with bcrypt (12 rounds)
- Creates user record (verified: false)
- Sends verification email
- Returns: 201 { id, email, created_at } | 409 | 400

## POST /auth/verify
- Input: { token: string }
- Validates token exists and not expired (24h)
- Sets user.verified = true
- Returns: 200 | 400
```

### tasks.md
```markdown
# Tasks

- [ ] Create Prisma migration for users table
- [ ] Implement User repository (CRUD)
- [ ] Create POST /auth/register endpoint
- [ ] Add email service (SendGrid integration)
- [ ] Create POST /auth/verify endpoint
- [ ] Write integration tests for all endpoints
- [ ] Update API documentation
```

## 5. Strengths
- Purpose-built for **brownfield** codebases (existing projects)
- Change isolation — each change gets its own folder
- Lightweight — no heavy ceremony, let you iterate freely
- No API keys, no MCP required
- Agent-agnostic (20+ agents supported)
- Two-folder model keeps current truth separate from proposed changes
- Easy to understand and adopt

## 6. Weaknesses / Criticisms
- Less mature than Spec Kit or BMAD
- No built-in quality gates or review stages
- Lighter weight may mean less guardrails
- Smaller community than top-starred tools
- Documentation still evolving

## 7. Adoption & Community
- Actively maintained by Fission AI
- Featured in multiple SDD comparison articles
- Recommended for brownfield change management by industry analysts
- OpenSpec 1.2 introduced new workflow capabilities (February 2026)

## 8. When to Choose This Tool
- You're working on **existing codebases** (brownfield, not greenfield)
- You need **change isolation** (multiple features in parallel)
- You want **lightweight** SDD without heavy ceremony
- You prefer **no API keys or MCP** setup
- You want **agent-agnostic** workflows
- You need to **evolve** existing specs, not just create new ones

## 9. Sources
- [GitHub Repository](https://github.com/Fission-AI/OpenSpec)
- [Official Website](https://openspec.dev/)
- [GitHub Releases](https://github.com/Fission-AI/OpenSpec/releases)
- [Redreamality: OpenSpec Deep Dive](https://redreamality.com/garden/notes/openspec-guide/)
- [Redreamality: BMAD vs spec-kit vs OpenSpec vs PromptX](https://redreamality.com/blog/-sddbmad-vs-spec-kit-vs-openspec-vs-promptx/)
- [Medium: GSD vs Spec Kit vs OpenSpec vs Taskmaster AI](https://medium.com/@richardhightower/agentic-coding-gsd-vs-spec-kit-vs-openspec-vs-taskmaster-ai-where-sdd-tools-diverge-0414dcb97e46)
- [Kilo AI: SDD with Spec Kit + Kilo Code](https://blog.kilo.ai/p/spec-driven-development-what-it-is)
