# 10 — Taskmaster AI

## 1. Overview
An AI-powered task management system designed to drop into Cursor, Lovable, Windsurf, Roo, and other editors. Parses PRDs into structured tasks, provides MCP integration, and supports multiple AI providers. Created by Eyal Toledano.

## 2. Key Data

| Attribute | Value |
|---|---|
| **Maker** | Eyal Toledano |
| **Type** | Open-source task management CLI + MCP server |
| **GitHub Repo** | eyaltoledano/claude-task-master |
| **License** | Open source |
| **Spec Format** | PRD text → auto-generated tasks (JSON) |
| **SDD Level** | Spec-first (PRD-driven) |
| **Agent Lock-in** | Multiple (supports various AI providers) |
| **Install** | `npm install -g task-master-ai && task-master init` |
| **Languages** | Language-agnostic |
| **Pricing** | Free |

## 3. How It Works

### Workflow
1. Write a detailed PRD (example template provided after init)
2. Parse PRD: `task-master parse-prd your-prd.txt`
3. List tasks: `task-master list`
4. Get next task: `task-master next`
5. Implement task with your AI agent
6. Mark complete and move to next

### MCP Integration
Works directly from your editor via Model Control Protocol. Tool modes:
- **Core** (7 tools) — ~70% token reduction
- **Standard** (15 tools) — balanced
- **All** (36 tools) — full feature set

### Multiple AI Providers
Supports Claude 3.7, GPT-4, Gemini, and more. Configure main model, research model, and fallback model.

### Cursor Integration
`.cursor/rules/dev_workflow.mdc` is auto-loaded, giving AI knowledge about the task management system.

## 4. Example Spec

### PRD Input
```markdown
# User Registration System PRD

## Overview
Build a user registration system with email verification for the mobile app.

## Requirements

### Functional
1. Users register with email and password
2. Email must be unique and valid format
3. Password: min 8 chars, 1 uppercase, 1 number
4. System sends verification email via SendGrid
5. Users verify email via link (24h expiry)
6. Login endpoint returns JWT (15min access, 7day refresh)

### Non-Functional
- Rate limiting: 5 registration attempts per IP per hour
- Passwords hashed with bcrypt (12 rounds)
- All endpoints return consistent error format

### Tech Stack
- Node.js + TypeScript + Express
- PostgreSQL + Prisma
- SendGrid for emails
- Vitest for testing
```

### Generated Tasks (after `task-master parse-prd`)
```json
[
  {
    "id": 1,
    "title": "Set up database schema",
    "description": "Create Prisma schema with users and verification_tokens tables",
    "status": "pending",
    "dependencies": [],
    "priority": "high"
  },
  {
    "id": 2,
    "title": "Implement User repository",
    "description": "Create repository layer for user CRUD operations",
    "status": "pending",
    "dependencies": [1],
    "priority": "high"
  },
  {
    "id": 3,
    "title": "Build registration endpoint",
    "description": "POST /auth/register with validation, hashing, and email sending",
    "status": "pending",
    "dependencies": [1, 2],
    "priority": "high"
  }
]
```

## 5. Strengths
- Excellent Cursor integration (auto-loaded rules)
- MCP support for editor-native experience
- Token-efficient core mode (70% reduction)
- Multiple AI provider support
- PRD-to-tasks pipeline is intuitive
- Task dependencies ensure correct order
- Many forks and community variations

## 6. Weaknesses / Criticisms
- Primarily designed for Cursor (other editors are secondary)
- Less structured spec process than Spec Kit or BMAD
- PRD parsing quality depends on PRD quality
- No built-in spec evolution (spec-first, not spec-anchored)
- Task decomposition can miss nuances

## 7. Adoption & Community
- Multiple forks on GitHub (kylantomita, stephanschielke, James-Cherished-Inc, etc.)
- Active development with regular updates
- Recommended for "task decomposition in Cursor" by industry comparisons
- Featured in Rick Hightower's SDD tool comparison

## 8. When to Choose This Tool
- You primarily use **Cursor** as your IDE
- You want **PRD-to-tasks** pipeline (not heavy spec workflows)
- You want **MCP integration** for editor-native experience
- You prefer **multiple AI providers** (not locked to one)
- You want a **lightweight** task management layer
- Token efficiency matters (core mode: 70% reduction)

## 9. Sources
- [GitHub Repository](https://github.com/eyaltoledano/claude-task-master)
- [Tutorial/Docs](https://github.com/eyaltoledano/claude-task-master/blob/main/docs/tutorial.md)
- [README](https://github.com/eyaltoledano/claude-task-master/blob/main/README-task-master.md)
- [Medium: GSD vs Spec Kit vs OpenSpec vs Taskmaster AI](https://medium.com/@richardhightower/agentic-coding-gsd-vs-spec-kit-vs-openspec-vs-taskmaster-ai-where-sdd-tools-diverge-0414dcb97e46)
