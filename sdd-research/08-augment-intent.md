# 08 — Augment Intent

## 1. Overview
A multi-agent orchestration workspace by Augment Code. Uses "living specs" — self-maintaining documents that update as code changes. Three-agent architecture: Coordinator (plans), Specialists (6 personas execute in parallel), Verifier (validates against spec). Each workspace runs in an isolated git worktree.

## 2. Key Data

| Attribute | Value |
|---|---|
| **Maker** | Augment Code |
| **Type** | Commercial desktop workspace |
| **GitHub Stars** | N/A (proprietary) |
| **License** | Proprietary |
| **Spec Format** | Living specs (auto-updating markdown) |
| **SDD Level** | Spec-anchored |
| **Agent Lock-in** | BYOA (Bring Your Own Agent) — supports Claude Code, Codex, OpenCode |
| **Platform** | macOS (Apple Silicon); Windows waitlist |
| **Languages** | Language-agnostic |
| **Pricing** | Standard: $60/month, Max: $200/month (up to 20 users, pooled credits) |

## 3. How It Works

### Three-Agent Architecture
1. **Coordinator** — Analyzes codebase, drafts specs, generates tasks
2. **Specialists** (6 personas) — Implementation, Architecture, Testing, Security, Performance, Documentation — execute in parallel
3. **Verifier** — Validates results against the spec before human review

### Living Specs
The key innovation: a self-maintaining document that serves as the source of truth. As code changes, the spec updates automatically, ensuring all agents and humans work from the same context.

### Context Engine
Processes 400,000+ files through semantic dependency analysis. Every agent shares deep understanding of your entire codebase.

### Isolated Workspaces
Each workspace is backed by its own git worktree — safe to explore changes without affecting other work.

## 4. Example Spec

### Living Spec (auto-generated and maintained)
```markdown
# Living Spec: User Registration

## Goal
Enable self-service user registration with email verification.

## Status: In Progress
- [x] Database schema designed
- [x] User model implemented
- [ ] Registration endpoint
- [ ] Email verification flow
- [ ] Integration tests

## Architecture Decisions
- Auth: JWT with refresh tokens (Coordinator decision, approved)
- Email: SendGrid transactional tier
- Rate limiting: 5 req/IP/hour via express-rate-limit

## Implementation Notes
- User model: src/models/user.ts (implemented by Implementation Specialist)
- Migration: prisma/migrations/001_users.sql (verified by Architecture Specialist)
- Security review: Password hashing uses bcrypt 12 rounds (approved by Security Specialist)

## Open Questions
- Should we support phone number registration in v2?

## Tasks (Auto-managed)
| Task | Specialist | Status |
|---|---|---|
| Prisma schema | Architecture | ✅ Complete |
| User repository | Implementation | ✅ Complete |
| Register endpoint | Implementation | 🔄 In Progress |
| Email service | Implementation | ⏳ Pending |
| Security scan | Security | ⏳ Pending |
| Integration tests | Testing | ⏳ Pending |
```

## 5. Strengths
- Living specs auto-update as code changes (no spec rot)
- Multi-agent orchestration with specialized personas
- Context Engine processes 400K+ files
- Isolated git worktrees per workspace
- BYOA — not locked to one agent
- Academic research backs 34.2% reduction in task completion time
- Verifier ensures spec compliance before human review

## 6. Weaknesses / Criticisms
- Proprietary and paid ($60-200/month)
- macOS only (Apple Silicon) — Windows not yet available
- Credit-based pricing may limit heavy use
- Newer tool — less community validation than open-source alternatives
- Requires learning a new workspace paradigm

## 7. Adoption & Community
- Public beta (early 2026)
- Active blog and documentation
- Featured in Augment Code's comparison articles
- Positioned as "what comes after the IDE"

## 8. When to Choose This Tool
- You want **multi-agent orchestration** with specialized roles
- You need **living specs** that auto-update (no spec rot)
- You work with **large codebases** (400K+ files)
- You want **isolated workspaces** (git worktrees)
- You're willing to pay for a **commercial tool**
- You want **BYOA** flexibility (not locked to one agent)

## 9. Sources
- [Official Product Page](https://www.augmentcode.com/product/intent)
- [Intent Docs](https://docs.augmentcode.com/intent/overview)
- [Augment Blog: Intent — A Workspace for Agent Orchestration](https://www.augmentcode.com/blog/intent-a-workspace-for-agent-orchestration)
- [Augment: What Is Spec-Driven Development?](https://www.augmentcode.com/guides/what-is-spec-driven-development)
- [Augment: SDD with Multi-Agent Systems](https://www.augmentcode.com/guides/spec-driven-ai-code-generation-with-multi-agent-systems)
- [Augment: Best SDD Tools 2026](https://www.augmentcode.com/tools/best-spec-driven-development-tools)
- [Augment: Intent vs Windsurf](https://www.augmentcode.com/tools/intent-vs-windsurf)
- [Ry Walker Research: Augment Intent](https://rywalker.com/research/augment-intent)
