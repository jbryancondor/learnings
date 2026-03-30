# 11 — Spec Kitty

## 1. Overview
An open-source CLI workflow for spec-driven development with Kanban dashboard, git worktree isolation, and auto-merge. The only SDD tool with built-in worktree management and parallel feature isolation. Offers two "missions": Software Dev Kitty (SDD workflow) and Deep Research Kitty (evidence gathering).

## 2. Key Data

| Attribute | Value |
|---|---|
| **Maker** | Priivacy AI |
| **Type** | Open-source CLI + Kanban dashboard |
| **License** | Open source |
| **Spec Format** | Markdown (spec → plan → tasks → implement → review → merge) |
| **SDD Level** | Spec-anchored |
| **Agent Lock-in** | None (Claude, Cursor, Gemini, Codex) |
| **Install** | `pip install spec-kitty-cli && spec-kitty init my-project --ai claude` |
| **Languages** | Language-agnostic |
| **Pricing** | Free |

## 3. How It Works

### Workflow
```
Spec → Plan → Tasks → Implement → Review → Merge
```

### Key Features
- **Kanban Dashboard** — Visual project tracking
- **Git Worktree Isolation** — Each feature runs in its own worktree
- **Auto-merge** — Completed features auto-merge when approved
- **Work Package Workflows** — Structured units of work
- **Repository-Native Artifacts** — Everything lives in the repo

### Two Missions
1. **Software Dev Kitty** — SDD workflow for shipping features (default)
2. **Deep Research Kitty** — Methodology for evidence gathering, analysis, synthesis

### Differentiator
Only SDD tool with **built-in worktree management and parallel feature isolation**. Multiple features can be developed simultaneously without interference.

## 4. Example Spec

### Initialize
```bash
spec-kitty init my-project --ai claude
```

### Feature Workflow
```bash
# Start a new feature
spec-kitty feature create user-registration

# Creates git worktree + spec structure:
# worktrees/user-registration/
#   .spec-kitty/
#     ├── spec.md         # Feature specification
#     ├── plan.md         # Technical plan
#     ├── tasks.md        # Implementation tasks
#     └── status.md       # Current progress

# Write spec
# spec.md:
```

```markdown
# Feature: User Registration

## Description
Email/password registration with verification for mobile app onboarding.

## Acceptance Criteria
- Valid email required (unique in system)
- Password: 8+ chars, 1 uppercase, 1 number
- Verification email sent on registration
- 201 response with user object (no password_hash)
- 409 for duplicate email

## Dependencies
- SendGrid API configured
- PostgreSQL database available

## Estimated Effort
Medium (3-5 tasks)
```

### Kanban View
```
| Spec      | Plan      | Implement  | Review    | Done      |
|-----------|-----------|------------|-----------|-----------|
| dark-mode | user-reg  | api-cache  | payments  | onboarding|
```

## 5. Strengths
- **Only tool with built-in worktree management** — parallel features without conflicts
- Kanban dashboard for visual tracking
- Auto-merge capability
- Two modes (dev + research)
- Streamlined artifacts to reduce token waste
- Focus on spec/plan stage to minimize babysitting during implementation

## 6. Weaknesses / Criticisms
- Smaller community than Spec Kit, BMAD, or Superpowers
- Requires Python for installation
- Less documentation than more established tools
- Newer — less battle-tested

## 7. Adoption & Community
- Featured in spec-compare research comparison
- Active development by Priivacy AI
- Available on PyPI (spec-kitty-cli)
- Recognized for unique worktree approach

## 8. When to Choose This Tool
- You need **parallel feature development** with isolation
- You want **git worktree** management built-in
- You prefer a **visual Kanban** dashboard
- You want **auto-merge** capabilities
- You work on **multiple features** simultaneously

## 9. Sources
- [GitHub Repository](https://github.com/Priivacy-ai/spec-kitty)
- [Documentation](https://priivacy-ai.github.io/spec-kitty/)
- [PyPI Package](https://pypi.org/project/spec-kitty-cli/)
- [spec-compare: 6 SDD Tools Compared](https://github.com/cameronsjo/spec-compare)
