# 09 — Ralph Loop (Ralph Wiggum)

## 1. Overview
An AI coding technique (not a framework) that runs AI agents in automated loops until specifications are fulfilled. Each iteration spawns a fresh agent process with a clean context window. The agent reads specs from disk, picks a task, implements it, commits, and exits. A bash loop restarts it. Created by Geoffrey Huntley.

## 2. Key Data

| Attribute | Value |
|---|---|
| **Creator** | Geoffrey Huntley |
| **Type** | Technique / pattern (multiple implementations) |
| **GitHub Stars** | Various implementations (smart-ralph, speckit-ralph, ralph-wiggum) |
| **License** | Various (mostly open source) |
| **Spec Format** | Any — works with any spec framework |
| **SDD Level** | Spec-first (loop ensures spec compliance) |
| **Agent Lock-in** | None (Claude Code, Cursor, Codex, Windsurf, Amp, OpenCode) |
| **Languages** | Language-agnostic |
| **Pricing** | Free |

## 3. How It Works

### The Loop Cycle
```
1. Orient — Read specs from disk
2. Pick Task — Select next incomplete task from the plan
3. Implement & Test — Code and verify
4. Commit & Push — Save progress to git
5. Output DONE — Signal completion of iteration
6. Bash loop checks — If tasks remain, restart with fresh context
```

### Key Innovation
Each iteration spawns a **new agent process** with a clean context window. Git is the memory layer. Unlike maintaining one long session (which degrades), Ralph embraces fresh starts.

### The Philosophy
"Instead of maintaining perfect context, embrace fresh starts and let git be the memory layer."

### Combining with SDD
The same thing that makes Ralph powerful (autonomy + repetition) also makes it risky: drift, broken assumptions, runaway changes. SDD specs provide the guardrails.

## 4. Example Spec

### The Loop (bash)
```bash
#!/bin/bash
while true; do
  claude-code --prompt "
    Read the specs in ./specs/ directory.
    Read the tasks in ./tasks.md.
    Pick the next incomplete task.
    Implement it following the spec.
    Run tests.
    If tests pass, commit and mark task complete.
    Output DONE when finished.
  "

  # Check if all tasks are complete
  if grep -q "- \[x\]" tasks.md && ! grep -q "- \[ \]" tasks.md; then
    echo "All tasks complete!"
    break
  fi

  echo "Restarting with fresh context..."
  sleep 2
done
```

### Spec it reads (compatible with any format)
```markdown
# User Registration Spec

## Endpoints
- POST /auth/register — Create new user account
- POST /auth/verify — Verify email with token

## Tasks
- [x] Create database schema
- [x] Implement User model
- [ ] Build registration endpoint
- [ ] Add email verification
- [ ] Write integration tests
```

## 5. Strengths
- Fresh context per iteration — no context window degradation
- Git as memory layer — simple, reliable, auditable
- Agent-agnostic — works with any coding agent
- Combines with any spec framework (Spec Kit, BMAD, OpenSpec, etc.)
- Enables **autonomous overnight coding**
- Real-world proof: developer shipped 100K LOC in 2 weeks
- Every commit traceable, git bisect finds exact bugs

## 6. Weaknesses / Criticisms
- Not a framework — a technique that needs a spec framework alongside it
- Risk of drift without strong specs and tests
- Autonomous loops can burn API credits fast
- Requires robust test suite to catch errors between iterations
- No built-in quality gates (relies on tests and spec frameworks)
- Can produce "whack-a-mole" bugs if specs are weak

## 7. Adoption & Community
- Multiple implementations on GitHub (smart-ralph, speckit-ralph, ralph-wiggum)
- awesome-ralph curated list of resources
- DevOps teams using it for CI/CD (auto-fix failing tests)
- 100K LOC shipped in 2 weeks case study
- Active Medium and blog community

## 8. When to Choose This Tool
- You want **autonomous overnight/weekend coding**
- You have a **strong test suite** as guardrails
- You already use an SDD framework and want to **automate execution**
- You want to **combine** with Spec Kit, BMAD, or OpenSpec for guardrails
- Context window degradation is a real problem
- You're comfortable with **fresh agent processes** per task

## 9. Sources
- [awesome-ralph (curated list)](https://github.com/snwfdhmp/awesome-ralph)
- [ralph-wiggum implementation](https://github.com/fstandhartinger/ralph-wiggum)
- [smart-ralph (Claude Code plugin)](https://github.com/tzachbon/smart-ralph)
- [speckit-ralph (Spec Kit integration)](https://github.com/merllinsbeard/speckit-ralph)
- [Medium: Ralph Wiggum Loops + SDD](https://new2026.medium.com/ralph-wiggum-loops-are-hot-right-now-heres-how-spec-driven-development-makes-them-actually-977bf8eb1959)
- [Alex Lavaee: 100K LOC in 2 Weeks](https://alexlavaee.me/blog/ai-coding-infrastructure/)
- [alexop.dev: SDD with Claude Code in Action](https://alexop.dev/posts/spec-driven-development-claude-code-in-action/)
- [jingles.dev: SDD 3-Step Framework](https://jingles.dev/articles/claude-spec-plan-loop)
- [Vibe Sparking: SDD Frameworks](https://www.vibesparking.com/en/blog/ai/2026-01-25-spec-driven-development-frameworks-bmad-gsd-ralph/)
