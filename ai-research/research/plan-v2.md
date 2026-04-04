# Generative AI Engineer — Deep Research Plan

**Version:** 2
**Date:** 2026-04-04
**Goal:** Build a comprehensive, state-of-the-art knowledge base to become a Generative AI Engineer.
**Seed article:** [The 8 Levels of Agentic Engineering](https://www.bassimeledath.com/blog/levels-of-agentic-engineering) — Bassim Eledath

---

## How to Use This Plan

This plan serves **two audiences** — read the part that applies to you:

| If you are... | Start here | Your sections |
|---|---|---|
| **Bryan** (the learner) | Part 1 | Part 1 (learning journey) + Part 2 (reference material) |
| **An AI research agent** | Part 3 | Part 3 (agent assignments) + Part 2 (reference material) |

**How this plan is organized:**

- **Part 1 — Your Learning Journey** lays out what to learn, in what order, and why. Start here. It progresses from foundational concepts to frontier territory, with clear checkpoints.
- **Part 2 — Reference Material** is a lookup section: company sources, competing frameworks, and source priority tiers. Consult it as needed — you don't read it top to bottom.
- **Part 3 — Agent Research Assignments** contains machine-parseable instructions for AI agents that will research and synthesize sources. If you're Bryan, you can skip this entirely until you want to review agent output.

**Reading order for Bryan:**
1. Skim the 8 Levels table (30 seconds — get the big picture)
2. Read the Learning Path to understand your progression
3. Do the Quick Start actions
4. Use the Technology Stack tables as a shopping list when you reach each level
5. Reference the Terminology section when you hit an unfamiliar term

---

## Table of Contents

- [Part 1: Your Learning Journey](#part-1-your-learning-journey)
  - [Progress Tracker](#progress-tracker)
  - [The 8 Levels at a Glance](#the-8-levels-at-a-glance)
  - [Learning Path & Progression Map](#learning-path--progression-map) (includes Concept Dependency Tree)
  - [Quick Start — What to Do First](#quick-start--what-to-do-first)
  - [Technology Stack by Level](#technology-stack-by-level)
  - [Key Terminology by Level](#key-terminology-by-level)
- [Part 2: Reference Material](#part-2-reference-material)
  - [Company Index](#company-index)
  - [Competing Maturity Models](#competing-maturity-models)
  - [Source Priority Tiers](#source-priority-tiers)
- [Part 3: Agent Research Assignments](#part-3-agent-research-assignments)
  - [How Agents Should Use This Section](#how-agents-should-use-this-section)
  - [Research Folder Structure & File Schema](#research-folder-structure--file-schema)
  - [Agent 1 — Agentic Taxonomies & Competing Frameworks](#agent-1--agentic-taxonomies--competing-frameworks)
  - [Agent 2 — Company Case Studies](#agent-2--company-case-studies)
  - [Agent 3 — Tools & Protocols Landscape](#agent-3--tools--protocols-landscape)
  - [Agent 4 — Orchestration & Background Agent Patterns](#agent-4--orchestration--background-agent-patterns)
  - [Agent 5 — AI Terminology & Concepts Glossary](#agent-5--ai-terminology--concepts-glossary)
  - [Success Criteria](#success-criteria)
  - [Agent Status Dashboard](#agent-status-dashboard)

---

# Part 1: Your Learning Journey

> This section is for **Bryan**. It maps the concepts, tools, and skills you need — organized as a progression from fundamentals to frontier.

## Progress Tracker

Use this checklist to track where you are. Each level has a concrete "done when" milestone.

- [ ] **Level 1: Tab Complete** — Installed Copilot, used it daily for a week
- [ ] **Level 2: Agent IDE** — Built or modified a feature using Cursor/Windsurf
- [ ] **Level 3: Context Engineering** — Wrote a CLAUDE.md or .cursorrules, optimized a prompt for a real task
- [ ] **Level 4: Compounding Engineering** — Your rules file evolved across 3+ sessions; used SDD on a project
- [ ] **Level 5: MCP & Skills** — Connected an agent to an external tool (DB, API, or CI) via MCP
- [ ] **Level 6: Harness Engineering** — Set up observability (LangSmith/Langfuse) and a CI feedback loop for an agent
- [ ] **Level 7: Background Agents** — Ran an agent headless that produced a PR without you watching
- [ ] **Level 8: Autonomous Teams** — Orchestrated 2+ agents coordinating on a task with no human in the loop

---

## The 8 Levels at a Glance

These levels describe the maturity of how engineers work with AI. Each level builds on the previous ones.

| Level | Name | Core Idea | You'll Learn To... |
|---|---|---|---|
| 1 | Tab Complete | Copilot-style autocomplete | Use AI suggestions while you type |
| 2 | Agent IDE | Cursor-style multi-file AI editing | Have AI edit across files with context |
| 3 | Context Engineering | Token optimization, system prompts, memory | Control what the AI sees for better results |
| 4 | Compounding Engineering | Plan → Delegate → Assess → Codify loop | Make each AI session improve the next |
| 5 | MCP & Skills | Model Context Protocol, tools, APIs, CI pipelines | Give agents access to real tools and systems |
| 6 | Harness Engineering | Observability, feedback loops, backpressure, security | Build the safety net around your agents |
| 7 | Background Agents | Async multi-worker orchestration | Run agents without watching them |
| 8 | Autonomous Agent Teams | Agent-to-agent coordination, no human loop | Let agents coordinate with each other |

---

## Learning Path & Progression Map

The 8 levels are **mostly linear with two parallel tracks after Level 3**. Here's the progression:

```
Level 1 (Tab Complete) ──→ Level 2 (Agent IDE) ──→ Level 3 (Context Engineering)
                                                          │
                                                    ┌─────┴─────┐
                                                    ▼           ▼
                                              Level 4        Level 5
                                           (Compounding)   (MCP & Skills)
                                                    │           │
                                                    └─────┬─────┘
                                                          ▼
                                                    Level 6 (Harness Engineering)
                                                          │
                                                          ▼
                                                    Level 7 (Background Agents)
                                                          │
                                                          ▼
                                                    Level 8 (Autonomous Teams)
```

**Why this order:**

- **Levels 1 → 2 → 3 are strictly sequential.** You can't engineer context (L3) without first experiencing what an AI IDE does (L2), and L2 is meaningless without basic autocomplete intuition (L1).
- **Levels 4 and 5 can be learned in parallel.** Compounding Engineering (codifying rules) and MCP/Skills (giving agents tools) are independent capabilities that both build on Context Engineering.
- **Level 6 requires both 4 and 5.** You can't build a harness around an agent unless you understand both its rule system and its tool connections.
- **Levels 7 → 8 are strictly sequential** and require everything below.

### Level Dependencies

| To reach... | You must first complete... | Type |
|---|---|---|
| Level 2 | Level 1 | Hard — need autocomplete intuition |
| Level 3 | Level 2 + Foundation terms | Hard — context engineering requires understanding tokens, prompts |
| Level 4 | Level 3 | Hard — compounding requires context engineering knowledge |
| Level 5 | Level 3 | Hard — MCP extends context with external tools |
| Level 6 | Level 4 + Level 5 | Hard — harness wraps both rules and tools |
| Level 7 | Level 6 | Hard — background agents need harness for safety |
| Level 8 | Level 7 | Hard — autonomous teams = background agents coordinating |

### Concept Dependency Tree

Beyond levels, individual concepts chain into each other. Here are the key prerequisite chains:

```
Tokenization → Context Window → Context Engineering → Compounding Engineering
                                       ↓
                                 CLAUDE.md / AGENTS.md → SDD (Spec-Driven Development)

Prompt Engineering → System Prompt → Few-shot/Zero-shot → Chain of Thought → ReAct Pattern

Tool Use / Function Calling → MCP → Skills → Agent Framework

Hallucination → Grounding → RAG → Vector Database → Memory Bank

LLM-as-Judge → Evaluation over Review → Harness Engineering → Backpressure

Orchestration → Background Agents → Supervisory Engineering → Middle Loop
                                          ↓
                                   Autonomous Teams → Regenerative Architecture
```

> **Tip:** If you encounter a concept you don't understand, trace it leftward in the chains above to find what prerequisite you're missing.

---

## Quick Start — What to Do First

Do these 5 actions in order. They take you from zero to Level 3 — the gateway to everything above.

| # | Action | Why | Done when... |
|---|---|---|---|
| 1 | **Read the seed article** — Bassim Eledath's [8 Levels of Agentic Engineering](https://www.bassimeledath.com/blog/levels-of-agentic-engineering) | This gives you the mental model everything else hangs on. | You can explain each level in one sentence (~15 min) |
| 2 | **Learn the Foundation terms** — Items 1–10 in the [Terminology section](#key-terminology-by-level) below | These are the building blocks every later concept assumes. If you already know them, skim to confirm. | You can define tokenization, context window, system prompt, and grounding without looking them up |
| 3 | **Install your tools** — GitHub Copilot (L1) + Cursor or Windsurf (L2) + Claude Code CLI (L3–7) | Learning by doing > reading about doing. Get hands-on immediately. | All three tools installed and working in a real project |
| 4 | **Set up CLAUDE.md in a real project** | This is the bridge from L2 to L3. Writing a rules file forces you to think about what context the AI needs. | You have a working CLAUDE.md that improves agent output on your project |
| 5 | **Read Martin Fowler #23** — [Context Engineering for Coding Agents](https://martinfowler.com/articles/exploring-gen-ai/context-engineering-coding-agents.html) | The single best article for understanding Level 3, which is the gateway to everything above it. | You can explain context engineering and why it matters (~30 min) |

---

## Technology Stack by Level

Each level introduces new tools. Use these tables as a shopping list — adopt tools as you reach each level.

> **Legend:** ✅ Adoptable now | 🔬 Research only | 📖 Reference (not publicly available)

---

### Level 1 — Tab Complete
> Goal: AI-powered inline code suggestions inside your editor.

| Tool | Type | Status | Notes |
|---|---|---|---|
| GitHub Copilot | VS Code / JetBrains extension | ✅ | Industry standard, $10/mo Pro plan |
| Tabnine | Extension (any IDE) | ✅ | Privacy-first, runs locally |
| Codeium | Extension / standalone | ✅ | Free tier, built into Windsurf |
| Amazon Q Developer | Extension | ✅ | AWS-focused inline completions |

---

### Level 2 — Agent IDE
> Goal: Multi-file AI editing with chat, context awareness, and codebase indexing.

| Tool | Type | Status | Notes |
|---|---|---|---|
| **Cursor** | AI-first IDE (VS Code fork) | ✅ | Largest community, `.cursorrules` support |
| **Windsurf** | AI-first IDE (Codeium) | ✅ | Best price/feature ratio ($15/mo), Cascade agent |
| **GitHub Copilot Workspace** | Cloud IDE + agent | ✅ | Tight GitHub integration, task-to-PR flow |
| **VS Code + Copilot Chat** | Extension on existing IDE | ✅ | Lowest friction if already on VS Code |
| **JetBrains AI Assistant** | Plugin | ✅ | Best for Java/Kotlin/Python ecosystems |
| **Google Antigravity** | Agentic IDE | ✅ | True multi-agent orchestration + built-in browser (2025) |
| **Amazon Kiro** | Agentic IDE (SDD-first) | ✅ | Spec-driven development + hooks; only IDE with SDD built-in |

---

### Level 3 — Context Engineering
> Goal: Control what the AI sees. Optimize every token for accuracy and relevance.

| Tool | Type | Status | Notes |
|---|---|---|---|
| **CLAUDE.md** | Rules file (Claude Code) | ✅ | Persistent instructions injected into every session |
| **AGENTS.md** | Rules file (any agent) | ✅ | Agent-agnostic conventions file |
| **.cursorrules** | Rules file (Cursor) | ✅ | Cursor-specific context rules |
| **.windsurfrules** | Rules file (Windsurf) | ✅ | Windsurf-specific context rules |
| **Mem0** | Memory library | ✅ | Persistent user/session memory for LLM apps |
| **MemGPT** | Memory agent framework | ✅ | Long-term memory via virtual context management |
| **MemOS** | Memory OS for AI | 🔬 | arXiv 2025 — memory as a first-class OS layer |
| **Amazon Kiro hooks** | Automation hooks | ✅ | Auto-trigger agent actions on file/event changes |

---

### Level 4 — Compounding Engineering
> Goal: Each AI session improves the next. Codify learnings into rules files automatically.

| Tool | Type | Status | Notes |
|---|---|---|---|
| **Claude Code** | CLI agent | ✅ | Native CLAUDE.md loop; plan → delegate → assess → codify |
| **Cursor + rules** | IDE | ✅ | `.cursorrules` updated after each session |
| **Amazon Kiro + specs** | IDE | ✅ | Spec files evolve alongside the codebase |
| **GitHub Spec-Kit** | Open-source SDD tool | ✅ | Places spec at the centre of the dev process |

---

### Level 5 — MCP & Skills
> Goal: Give the agent hands. Connect it to databases, APIs, CI pipelines, browsers.

| Tool | Type | Status | Notes |
|---|---|---|---|
| **MCP (Model Context Protocol)** | Open protocol | ✅ | Standard by Anthropic (Nov 2024); 97M monthly SDK downloads as of Feb 2026 |
| **A2A (Agent-to-Agent Protocol)** | Open protocol | ✅ | Google's complementary protocol for agent-to-agent communication; both now under Linux Foundation AAIF (Dec 2025) |
| **MCPM** | CLI package manager | ✅ | `mcpm install <server>` — discovers, installs, configures MCP servers |
| **MCP Servers (official)** | Collection | ✅ | github.com/modelcontextprotocol/servers — filesystem, GitHub, Slack, DB, browser |
| **Claude Code skills** | Custom skills | ✅ | `.claude/skills/` — reusable agent behaviors triggered by slash commands |
| **fast-agent** | CLI framework | ✅ | Creates sophisticated agents/workflows via CLI with MCP support |
| **PulseMCP** | MCP registry | ✅ | pulsemcp.com — discover 546+ MCP clients and servers |

---

### Level 6 — Harness Engineering
> Goal: Build the environment around the agent — observability, feedback loops, guardrails.

| Tool | Type | Status | Notes |
|---|---|---|---|
| **LangSmith** | LLM observability | ✅ | Tracing, evaluation, dataset management (LangChain) |
| **Langfuse** | LLM observability | ✅ | Open-source alternative to LangSmith |
| **Helicone** | LLM proxy + observability | ✅ | Drop-in proxy, logs all LLM calls |
| **Braintrust** | Eval platform | ✅ | LLM-as-judge evaluations, CI integration |
| **Claude Code hooks** | Harness automation | ✅ | Pre/post tool-call hooks in `settings.json` |
| **GitHub Actions / CI** | CI/CD | ✅ | Automated feedback loop — agent opens PR, CI validates |
| **Gitleaks** | Secret scanning | ✅ | Runs on every push; catches secrets before deploy |

---

### Level 7 — Background Agents
> Goal: Agents run async, without you watching. Orchestrate multiple workers across tasks.

| Tool | Type | Status | Notes |
|---|---|---|---|
| **Claude Code** (background mode) | CLI | ✅ | Run headless, pipe output, spawn subagents |
| **OpenAI Codex CLI** | CLI agent | ✅ | Background coding agent from OpenAI, desktop command center |
| **Dispatch** | Orchestrator tool | 🔬 | Bassim Eledath's internal tool — manages workers across different models |
| **Spotify Honk** | Internal agent | 📖 | Spotify's background coding agent — 1,500+ PRs, not public but documented |
| **LangGraph** | Agent orchestration | ✅ | State machine for multi-step agentic workflows |
| **Claude Agent SDK** | SDK | ✅ | Security-first production agent orchestration |
| **OpenAI Agents SDK** | SDK | ✅ | Delegation patterns, handoff between agents |

---

### Level 8 — Autonomous Agent Teams
> Goal: Agents coordinate directly. No central human loop. Frontier territory.

| Tool | Type | Status | Notes |
|---|---|---|---|
| **Google Antigravity** | Agentic IDE | ✅ | Only consumer tool with true multi-agent orchestration today |
| **AutoGen (Microsoft)** | Framework | ✅ | Multi-agent conversation framework; agents as actors |
| **CrewAI** | Framework | ✅ | Role-based multi-agent crews with task delegation |
| **LangGraph** | Framework | ✅ | Graph-based agent coordination, cycles, branching |
| **Claude Agent SDK** | SDK | ✅ | Anthropic's production-grade agent orchestration |
| **A2A Protocol** | Protocol | ✅ | Direct agent-to-agent communication standard |
| **mcp-agent** | Library | ✅ | github.com/lastmile-ai/mcp-agent — build agents using MCP + workflow patterns |

---

### Protocols & Standards (Cross-Level)

| Protocol | Created by | Year | Purpose |
|---|---|---|---|
| **MCP** (Model Context Protocol) | Anthropic → Linux Foundation AAIF | Nov 2024 | Standard for connecting AI to tools, APIs, data sources |
| **A2A** (Agent-to-Agent) | Google → Linux Foundation AAIF | 2025 | Standard for direct agent-to-agent communication |

> Both MCP and A2A are now governed by the **Agentic AI Foundation (AAIF)** under the Linux Foundation, co-founded by: Anthropic, OpenAI, Google, Microsoft, AWS, Block (Dec 2025).

---

## Key Terminology by Level

> Learn the terms for each level as you progress. Terms marked with **★** are prerequisite — understand them before moving on to the next level. Terms are ordered within each group so earlier ones feed into later ones.

### Foundation (learn before starting — prerequisites for all levels)

| # | Term | Definition |
|---|---|---|
| 1 | ★ **Tokenization / Token Budget** | How LLMs break text into units; the budget is how many tokens you can send/receive |
| 2 | ★ **Context Window** | The maximum number of tokens an LLM can process in a single interaction |
| 3 | **Embeddings** | Numerical vector representations of text that capture semantic meaning |
| 4 | ★ **Hallucination** | When an LLM generates plausible-sounding but factually incorrect output |
| 5 | **Temperature / Top-p** | Parameters controlling randomness in LLM output; lower = more deterministic |
| 6 | ★ **System Prompt** | Hidden instructions that set the LLM's behavior, role, and constraints |
| 7 | ★ **Prompt Engineering** | The practice of crafting inputs to get optimal LLM outputs |
| 8 | **Few-shot / Zero-shot Prompting** | Providing examples (few-shot) or no examples (zero-shot) to guide the LLM |
| 9 | **Fine-tuning vs Prompting** | Training a model on custom data vs guiding it through prompt design |
| 10 | ★ **Grounding** | Anchoring LLM outputs to verified facts or source material to reduce hallucination |

### Level 1–2: AI-Assisted Coding

| # | Term | Definition |
|---|---|---|
| 11 | **AI Pair Programming** | Using AI as a real-time coding partner for suggestions, reviews, and generation |
| 12 | **Vibe Coding** | Generating code through natural language prompts with minimal manual editing (coined by Andrej Karpathy, Feb 2025) |
| 13 | **Vibe Coding Hangover** | The technical debt and maintenance burden from code you generated but don't understand |
| 14 | **AI Fluency** | The skill of communicating effectively with AI tools to get useful results |

### Level 3: Context Engineering

| # | Term | Definition |
|---|---|---|
| 15 | ★ **Context Engineering** | The discipline of optimizing what information the AI sees — token-efficient, relevant, and structured |
| 16 | **RAG (Retrieval-Augmented Generation)** | Fetching external documents at query time to inject relevant context into the LLM |
| 17 | **Vector Database** | A database optimized for storing and querying embeddings (e.g., Pinecone, Chroma) |
| 18 | ★ **AGENTS.md / CLAUDE.md** | Convention files that provide persistent instructions and context to AI agents |
| 19 | **Memory Bank** | Persistent storage that lets agents recall information across sessions |
| 20 | **Anchoring to a Reference Application** | Using a known-good codebase as ground truth for AI to reference |

### Level 4: Compounding Engineering

| # | Term | Definition |
|---|---|---|
| 21 | ★ **Compounding Engineering** | The practice where each AI session improves the next via codified rules and specs |
| 22 | **SDD (Spec-Driven Development)** | Writing specifications first, then having AI generate code from them |
| 23 | **Spec-Kit (GitHub)** | GitHub's open-source tool for spec-driven development workflows |
| 24 | **Amazon Kiro** | AWS's SDD-first agentic IDE with built-in spec management and hooks |
| 25 | **Tessl** | AI-first IDE focused on spec-driven development |

### Level 5: MCP & Skills

| # | Term | Definition |
|---|---|---|
| 26 | ★ **MCP (Model Context Protocol)** | Open protocol (Anthropic, Nov 2024) for connecting AI to tools, APIs, and data sources |
| 27 | ★ **Tool Use / Function Calling** | The ability for an LLM to invoke external functions and APIs |
| 28 | **Skills (MCP Skills)** | Reusable agent behaviors triggered by commands (e.g., `.claude/skills/`) |
| 29 | **Agent Framework** | Libraries for building AI agents (e.g., LangChain, CrewAI, AutoGen) |
| 30 | **Chain of Thought (CoT)** | Prompting technique where the LLM reasons step-by-step before answering |
| 31 | **ReAct Pattern** | Combining reasoning (Re) and acting (Act) — the agent thinks, then calls tools, then thinks again |

### Level 6: Harness Engineering

| # | Term | Definition |
|---|---|---|
| 32 | ★ **Harness Engineering** | Building the environment around the agent — observability, feedback loops, guardrails, security |
| 33 | **Backpressure (AI systems)** | Mechanisms to slow down or queue agent work when downstream systems are overwhelmed |
| 34 | **LLM-as-Judge** | Using one LLM to evaluate the output quality of another LLM |
| 35 | **Evaluation over Review** | Replacing manual code review with automated LLM evaluation (Ankit Jain) |
| 36 | **Compound AI Systems** | Systems that combine multiple AI models, retrievers, and tools into one pipeline |

### Level 7: Background Agents

| # | Term | Definition |
|---|---|---|
| 37 | ★ **Agentic Engineering** | The practice of building, deploying, and managing autonomous AI coding agents |
| 38 | ★ **Background Agents** | AI agents that run asynchronously without human supervision |
| 39 | **Orchestration** | Coordinating multiple agents or steps in a workflow (routing, delegation, sequencing) |
| 40 | **Autonomous Development Loop** | A cycle where agents plan, code, test, and iterate without human intervention |
| 41 | **Multi-Model Systems** | Architectures using different LLMs for different tasks (e.g., fast model for triage, strong model for code) |
| 42 | **Supervisory Engineering** | The human role of overseeing and directing autonomous agents (Annie Vella) |
| 43 | **Middle Loop** | The feedback cycle between the inner loop (agent coding) and outer loop (human review) |

### Level 8: Autonomous Agent Teams

| # | Term | Definition |
|---|---|---|
| 44 | **Regenerative Architecture** | System design where agents can modify and improve the architecture itself (Chad Fowler) |
| 45 | **AI Alignment** | Ensuring AI systems behave in accordance with human values and intentions |
| 46 | **MemOS** | Research concept (arXiv 2025) treating memory as a first-class OS layer for AI agents |

### Cross-Cutting (reference anytime)

| Term | Relevant at |
|---|---|
| **Compound AI Systems** | L5+ (systems combining multiple models and tools) |
| **A2A Protocol** | L5 and L8 (Google's agent-to-agent communication standard) |

---

# Part 2: Reference Material

> Lookup section — consult as needed. You don't need to read this top to bottom.

---

## Company Index

Sources grouped by company, ordered by research priority.

> **Reading priority:** 🔴 Read first (primary case studies) | 🟡 Read second | 🟢 Reference

---

### 🔴 Spotify
> Evidence of Level 7 (Background Agents). Built "Honk" — background coding agent producing 1,500+ merged PRs.

| # | Title | Date | URL |
|---|---|---|---|
| 1 | 1,500+ PRs Later: Spotify's Journey with Background Coding Agent (Honk, Part 1) | Nov 2025 | https://engineering.atspotify.com/2025/11/spotifys-background-coding-agent-part-1 |
| 2 | Context Engineering for Background Coding Agents (Honk, Part 2) | Nov 2025 | https://engineering.atspotify.com/2025/11/context-engineering-background-coding-agents-part-2 |
| 3 | Predictable Results Through Strong Feedback Loops (Honk, Part 3) | Dec 2025 | https://engineering.atspotify.com/2025/12/feedback-loops-background-coding-agents-part-3 |
| 4 | Our Multi-Agent Architecture for Smarter Advertising | Feb 2026 | https://engineering.atspotify.com/2026/2/our-multi-agent-architecture-for-smarter-advertising |

---

### 🔴 Martin Fowler / Thoughtworks
> Most comprehensive practitioner series on GenAI in software engineering (25 articles, 2023–2026). Focus on entries #18–#25.

| # | Title | Date | URL |
|---|---|---|---|
| 18 | Partner with the AI, throw away the code | Jul 2025 | https://martinfowler.com/articles/exploring-gen-ai/partner-with-ai-and-throw-away-the-code.html |
| 19 | To vibe or not to vibe | Sep 2025 | https://martinfowler.com/articles/exploring-gen-ai/to-vibe-or-not-vibe.html |
| 20 | Anchoring AI to a reference application | Sep 2025 | https://martinfowler.com/articles/exploring-gen-ai/anchoring-to-reference.html |
| 21 | Understanding Spec-Driven-Development: Kiro, spec-kit, and Tessl | Oct 2025 | https://martinfowler.com/articles/exploring-gen-ai/sdd-3-tools.html |
| 22 | Assessing internal quality while coding with an agent | Jan 2026 | https://martinfowler.com/articles/exploring-gen-ai/ccmenu-quality.html |
| 23 | Context Engineering for Coding Agents | Feb 2026 | https://martinfowler.com/articles/exploring-gen-ai/context-engineering-coding-agents.html |
| 24 | Harness Engineering — first thoughts | Feb 2026 | https://martinfowler.com/articles/exploring-gen-ai/harness-engineering-memo.html |
| 25 | Humans and Agents in Software Engineering Loops | Mar 2026 | https://martinfowler.com/articles/exploring-gen-ai/humans-and-agents.html |
| — | Fragments: March 16 (Supervisory Engineering, Yegge, Chad Fowler) | Mar 2026 | https://martinfowler.com/fragments/2026-03-16.html |
| — | SDD — Thoughtworks blog | 2025 | https://www.thoughtworks.com/en-us/insights/blog/agile-engineering-practices/spec-driven-development-unpacking-2025-new-engineering-practices |

---

### 🟡 Microsoft
> Agentic AI maturity model + AI-led SDLC with Azure and GitHub.

| Title | Date | URL |
|---|---|---|
| Agentic AI Adoption Maturity Model | 2025 | https://learn.microsoft.com/en-us/microsoft-copilot-studio/guidance/maturity-model-overview |
| An AI-led SDLC with Azure and GitHub | 2025 | https://techcommunity.microsoft.com/blog/appsonazureblog/an-ai-led-sdlc-building-an-end-to-end-agentic-software-development-lifecycle-wit/4491896 |

---

### 🟡 GitHub
> GitHub Copilot evolution, Spec-Kit (open-source SDD tool).

| Title | Date | URL |
|---|---|---|
| GitHub Spec-Kit — spec-driven.md | 2025 | https://github.com/github/spec-kit/blob/main/spec-driven.md |

---

### 🟡 Amazon / AWS
> Amazon Kiro — SDD-first IDE tool.

| Title | Date | URL |
|---|---|---|
| Amazon Kiro (SDD tool) | 2025 | TBD — search required |

---

### 🟡 Anthropic
> 16-agent C compiler case, Claude Code patterns, CLAUDE.md / AGENTS.md.

| Title | Date | URL |
|---|---|---|
| Anthropic multi-agent compiler | TBD | TBD — search required |

---

### 🟢 Gartner
> Industry analyst perspective — 80% of engineers need upskill by 2027.

| Title | Date | URL |
|---|---|---|
| Gartner: GenAI will require 80% of engineering workforce to upskill | Oct 2024 | https://www.gartner.com/en/newsroom/press-releases/2024-10-03-gartner-says-generative-ai-will-require-80-percent-of-engineering-workforce-to-upskill-through-2027 |
| Gartner Agentic AI Maturity Roadmap | 2025 | https://www.gartner.com/en/documents/6825634 |

---

### 🟢 Google
> Addy Osmani (Chrome DevRel) — LLM coding workflow 2026.

| Title | Date | URL |
|---|---|---|
| My LLM coding workflow going into 2026 — Addy Osmani | Dec 2025 | https://addyosmani.com/blog/ai-coding-workflow/ |

---

### 🟢 MIT Technology Review

| Title | Date | URL |
|---|---|---|
| From vibe coding to context engineering: 2025 in software development | Nov 2025 | https://www.technologyreview.com/2025/11/05/1127477/from-vibe-coding-to-context-engineering-2025-in-software-development/ |

---

### 🟢 Newsletters & Independent Authors

| Title | Author | Date | URL |
|---|---|---|---|
| Software engineering with LLMs in 2025: reality check | The Pragmatic Engineer | 2025 | https://newsletter.pragmaticengineer.com/p/software-engineering-with-llms-in-2025 |
| Spec Driven Development (SDD): The Evolution Beyond Vibe Coding | Daniel Sogl / Medium | 2025 | https://danielsogl.medium.com/spec-driven-development-sdd-the-evolution-beyond-vibe-coding-1e431ae7d47b |
| Deep: How Spotify is using AI Agents to manage tech debt | Dept of Product / Substack | 2025 | https://departmentofproduct.substack.com/p/deep-how-spotify-is-using-ai-agents |
| Agentic Coding: Spotify's Lessons Learned | Dawn Liphardt | 2025 | https://www.dawnliphardt.com/agentic-coding-spotifys-lessons-learned/ |
| AI Engineering Trends in 2025: Agents, MCP and Vibe Coding | The New Stack | Dec 2025 | https://ricmac.org/2025/12/22/ai-engineering-trends-in-2025-agents-mcp-and-vibe-coding/ |
| Memory for AI Agents: A New Paradigm of Context Engineering | The New Stack | 2025 | https://thenewstack.io/memory-for-ai-agents-a-new-paradigm-of-context-engineering/ |
| Generative AI Engineer Roadmap 2026 | JavaGuides | Dec 2025 | https://www.javaguides.net/2025/12/generative-ai-engineer-roadmap-2026.html |

---

## Competing Maturity Models

Multiple frameworks describe the progression of AI-assisted engineering. Understanding all of them helps you see the field from different angles.

| Model | Author / Company | Levels | URL |
|---|---|---|---|
| 8 Levels of Agentic Engineering | Bassim Eledath | 8 | https://www.bassimeledath.com/blog/levels-of-agentic-engineering |
| Steve Yegge's Framework | Steve Yegge | 0 → custom orchestrators w/ 10+ agents | TBD — mentioned in Martin Fowler March 2026 |
| Agentic AI Maturity Model | Microsoft Copilot Studio | L100–L500 | https://learn.microsoft.com/en-us/microsoft-copilot-studio/guidance/maturity-model-overview |
| Crawl / Walk / Run / Scale | Nexocode / Dextralabs | L1–L4 | https://nexocode.com/blog/posts/the-agentic-ai-maturity-model-crawl-walk-run-scale/ |
| Gartner Agentic AI Maturity Roadmap | Gartner | 5 stages | https://www.gartner.com/en/documents/6825634 |

---

## Source Priority Tiers

### Tier 1 — Must process (confirmed high-value, Q4 2025 / 2026)
- Spotify Honk 3-part series (Nov–Dec 2025)
- Martin Fowler Exploring GenAI #18–#25 (Jul 2025 – Mar 2026)
- Martin Fowler Fragments March 2026
- MIT Technology Review — From vibe coding to context engineering (Nov 2025)
- Addy Osmani — LLM coding workflow 2026
- Thoughtworks — SDD blog post

### Tier 2 — High value, process after Tier 1
- Microsoft — Agentic AI Maturity Model
- Bassim Eledath — 8 Levels article
- Amplifi Labs — AI Coding Glossary
- The New Stack — AI Engineering Trends 2025
- Pragmatic Engineer — LLMs in 2025 reality check
- Spotify Multi-Agent Advertising Architecture (Feb 2026)

### Tier 3 — Discover and process
- Steve Yegge's competing framework (URL unknown — search required)
- Anthropic case studies (URLs unknown — search required)
- Amazon Kiro docs/blog
- arxiv papers on multi-agent systems
- LinkedIn articles on AI fluency, context engineering, SDD

---

# Part 3: Agent Research Assignments

> This section is for **AI research agents**. Each assignment is self-contained and machine-parseable.

---

## How Agents Should Use This Section

1. **Find your assignment** by agent number (Agent 1, 2, 3a, 3b, 4, 5)
2. Each assignment contains everything you need: mission, output folder, confirmed sources, and search queries
3. **Write output files** to the specified folder using the file schema below
4. **Priority rule:** Process Q4 2025 and 2026 sources first
5. **Cross-reference:** If you discover sources relevant to another agent, note them in your output file under `## Related Terms` or `## See Also`

---

## Research Folder Structure & File Schema

### Folder structure

```
research/
├── plan.md                          ← v0 plan (original)
├── plan-v1.md                       ← v1 plan (preliminary research)
├── plan-v2.md                       ← THIS FILE (v2 — current)
├── INDEX.md                         ← master index of all sources (auto-updated by agents)
├── taxonomies/                      ← Agent 1: maturity models & frameworks
│   └── <article-slug>.md
├── company-cases/                   ← Agent 2: company case studies
│   └── <company-slug>.md
├── tools-protocols/
│   ├── ide/                         ← Agent 3a: IDE & authoring tools (Levels 1–4)
│   │   └── <tool-slug>.md
│   └── infra/                       ← Agent 3b: infrastructure & protocol tools (Levels 5–8)
│       └── <tool-slug>.md
├── orchestration-patterns/          ← Agent 4: multi-agent patterns & architecture
│   └── <pattern-slug>.md
└── terminology/                     ← Agent 5: glossary of AI engineering terms
    └── <term>.md
```

### File schema (every research file must follow this)

```markdown
---
source: <URL>
date_accessed: YYYY-MM-DD
published: YYYY-MM-DD
author: <name>
company: <company if applicable>
level_mapping: [1, 3, 5]   # which of the 8 agentic levels this maps to (optional)
tags: [context-engineering, mcp, spotify]
agent: <agent-name>
---

## Summary
## Key Concepts
## Quotes / Evidence
## Related Terms
## Relevance to Generative AI Engineer Role
```

---

## Agent 1 — Agentic Taxonomies & Competing Frameworks

| Field | Value |
|---|---|
| **Output folder** | `taxonomies/` |
| **Priority** | Q4 2025 and 2026 sources first |
| **Mission** | Map, compare, and synthesize the 5+ competing agentic maturity models. Find which companies align to which level. Cover Steve Yegge's framework specifically (referenced in Martin Fowler March 2026 but URL unknown). |

**Confirmed sources to process:**
- Bassim Eledath — 8 Levels (seed article)
- Martin Fowler — Fragments March 2026 (Supervisory Engineering, Yegge, Chad Fowler)
- Martin Fowler — Humans and Agents in Software Engineering Loops (Mar 2026)
- Microsoft — Agentic AI Maturity Model (L100–L500)
- Nexocode — Crawl/Walk/Run/Scale
- Gartner — Agentic AI Maturity Roadmap
- arxiv — AI Agents vs. Agentic AI: A Conceptual Taxonomy

**Search queries:**
- Steve Yegge agentic engineering framework levels 2025
- "compound AI systems" maturity model
- arxiv "agentic AI software engineering taxonomy 2025 2026"
- AI maturity model enterprise 2026 Forrester

---

## Agent 2 — Company Case Studies

| Field | Value |
|---|---|
| **Output folder** | `company-cases/` |
| **Priority** | Q4 2025 and 2026 sources first |
| **Mission** | Document real-world implementations by company. Spotify is the primary target (3-part Honk series). Also cover Anthropic, Microsoft, Google, GitHub/Amazon. |

**Confirmed sources to process:**
- Spotify Honk Part 1 (Nov 2025)
- Spotify Honk Part 2 (Nov 2025)
- Spotify Honk Part 3 (Dec 2025)
- Spotify Multi-Agent Architecture for Advertising (Feb 2026)
- Addy Osmani — LLM coding workflow 2026 (Google Chrome DevRel)
- Microsoft — AI-led SDLC with Azure and GitHub
- Dawn Liphardt — Agentic Coding: Spotify's Lessons Learned
- Dept of Product — How Spotify uses AI Agents to manage tech debt

**Search queries:**
- Anthropic background agents multi-agent case study 2025 2026
- Cursor autonomous agents production 2025
- GitHub Copilot Workspace real usage report 2025 2026
- Netflix / Uber / Airbnb AI agents engineering blog 2025 2026
- LinkedIn engineering AI agents production 2025 2026

---

## Agent 3a — IDE & Authoring Tools (Levels 1–4)

| Field | Value |
|---|---|
| **Output folder** | `tools-protocols/ide/` |
| **Model** | Sonnet 4.6 |
| **Priority** | Q4 2025 and 2026 sources first |
| **Mission** | Map all IDE and authoring tools a Generative AI Engineer uses at Levels 1–4. Cover AI-first IDEs, rules files (CLAUDE.md, AGENTS.md, .cursorrules), and SDD tools (Kiro, Spec-Kit, Tessl). |

**Confirmed sources to process:**
- Martin Fowler #21 — SDD: Kiro, spec-kit, and Tessl (Oct 2025)
- Martin Fowler #23 — Context Engineering for Coding Agents (Feb 2026)
- Martin Fowler #18 — Partner with the AI, throw away the code (Jul 2025)
- Martin Fowler #19 — To vibe or not to vibe (Sep 2025)
- Martin Fowler #20 — Anchoring AI to a reference application (Sep 2025)
- GitHub Spec-Kit — spec-driven.md
- Thoughtworks — SDD blog post
- Spotify Honk Part 2 — Context Engineering deep dive

**Search queries:**
- Claude Code CLAUDE.md AGENTS.md best practices 2025 2026
- Amazon Kiro SDD IDE review 2025
- Tessl AI-first IDE spec-driven 2025
- Cursor vs Windsurf vs Claude Code comparison 2026
- GitHub Copilot Workspace agentic features 2025

---

## Agent 3b — Infrastructure & Protocol Tools (Levels 5–8)

| Field | Value |
|---|---|
| **Output folder** | `tools-protocols/infra/` |
| **Model** | Sonnet 4.6 |
| **Priority** | Q4 2025 and 2026 sources first |
| **Mission** | Map all infrastructure-level tools: MCP ecosystem, A2A protocol, memory systems, harness/observability tooling. These are the tools that operate at and above Level 5. |

**Confirmed sources to process:**
- Martin Fowler #24 — Harness Engineering — first thoughts (Feb 2026)
- Amplifi Labs — Definitive Glossary (MCP, RAG, Tool Calling etc.)
- The New Stack — Memory for AI Agents (2025)

**Search queries:**
- "Model Context Protocol MCP" ecosystem servers 2025 2026
- MCPM MCP package manager CLI
- MemGPT Mem0 MemOS memory systems comparison 2025
- LLM observability tools LangSmith Langfuse Helicone 2025 2026
- A2A Agent-to-Agent protocol Google Linux Foundation 2025
- Harness engineering AI agents observability tools
- PulseMCP MCP registry 2026

---

## Agent 4 — Orchestration & Background Agent Patterns

| Field | Value |
|---|---|
| **Output folder** | `orchestration-patterns/` |
| **Priority** | Q4 2025 and 2026 sources first |
| **Mission** | Deep dive into multi-agent architecture patterns, design patterns, and the concepts introduced by Martin Fowler's recent entries. |

**Confirmed sources to process:**
- Martin Fowler #22 — Assessing internal quality while coding with an agent (Jan 2026)
- Martin Fowler #25 — Humans and Agents in Software Engineering Loops (Mar 2026)
- Martin Fowler Fragments — Supervisory Engineering, Middle Loop (Mar 2026)
- Spotify — Multi-Agent Architecture for Advertising (Feb 2026)
- arxiv — AI Agents vs. Agentic AI: A Conceptual Taxonomy

**New concepts to research (discovered in pre-research):**
- Supervisory Engineering / Middle Loop (Annie Vella)
- Regenerative Architecture (Chad Fowler)
- Evaluation over Review (Ankit Jain)
- Plan-and-Execute pattern
- Orchestrator / Worker separation
- Implementer vs Reviewer agent separation (Bassim Eledath)
- LLM-as-Judge pattern

**Search queries:**
- LangGraph multi-agent 2025 2026 production patterns
- AutoGen Microsoft multi-agent framework 2025
- CrewAI orchestration patterns 2025
- "plan execute" agent pattern LLM 2025
- LLM as judge evaluation pattern 2025
- ReAct chain of thought agent patterns
- Background agent dispatcher pattern 2025

---

## Agent 5 — AI Terminology & Concepts Glossary

| Field | Value |
|---|---|
| **Output folder** | `terminology/` |
| **Priority** | Cover all terms, especially those from Q4 2025 and 2026 articles |
| **Mission** | Define every key term in the Generative AI Engineer vocabulary. One file per term. Discover new terms from the articles found by other agents. |

**Full term list (46 terms, ordered by learning progression — define Foundation terms first, then level-by-level):**

_Foundation (define first — prerequisites for all levels):_
1. Tokenization / Token Budget, 2. Context Window, 3. Embeddings, 4. Hallucination, 5. Temperature / Top-p, 6. System Prompt, 7. Prompt Engineering, 8. Few-shot / Zero-shot Prompting, 9. Fine-tuning vs Prompting, 10. Grounding

_Level 1–2 (AI-Assisted Coding):_
11. AI Pair Programming, 12. Vibe Coding, 13. Vibe Coding Hangover, 14. AI Fluency

_Level 3 (Context Engineering):_
15. Context Engineering, 16. RAG (Retrieval-Augmented Generation), 17. Vector Database, 18. AGENTS.md / CLAUDE.md, 19. Memory Bank, 20. Anchoring to a Reference Application

_Level 4 (Compounding Engineering):_
21. Compounding Engineering, 22. SDD (Spec-Driven Development), 23. Spec-Kit (GitHub), 24. Amazon Kiro, 25. Tessl

_Level 5 (MCP & Skills):_
26. MCP (Model Context Protocol), 27. Tool Use / Function Calling, 28. Skills (MCP Skills), 29. Agent Framework, 30. Chain of Thought (CoT), 31. ReAct Pattern

_Level 6 (Harness Engineering):_
32. Harness Engineering, 33. Backpressure (AI systems), 34. LLM-as-Judge, 35. Evaluation over Review, 36. Compound AI Systems

_Level 7 (Background Agents):_
37. Agentic Engineering, 38. Background Agents, 39. Orchestration, 40. Autonomous Development Loop, 41. Multi-Model Systems, 42. Supervisory Engineering, 43. Middle Loop

_Level 8 (Autonomous Agent Teams):_
44. Regenerative Architecture, 45. AI Alignment, 46. MemOS

**Search queries:**
- Each term individually to find the canonical source/definition
- LinkedIn articles for: AI fluency, compounding engineering, context engineering 2025
- swyx.io, Simon Willison blog for emerging terminology
- Andrej Karpathy vibe coding original post Feb 2025

---

## Success Criteria

- [ ] At least 30 source articles researched across all agents
- [ ] At least 46 terminology entries defined (one file each, in learning progression order)
- [ ] Spotify Level 7 documented with all 4 primary sources
- [ ] All 5 competing maturity models compared in taxonomies/
- [ ] Steve Yegge's framework found and documented
- [ ] Martin Fowler Exploring GenAI #18–#25 all processed
- [ ] SDD tools (Kiro, Spec-Kit, Tessl) documented
- [ ] Company index in INDEX.md fully populated
- [ ] All files follow the standard schema
- [ ] Focus: 80%+ of sources from Q4 2025 or 2026

---

## Agent Status Dashboard

| Agent | Mission | Output Folder | Model | Status | Files Created |
|---|---|---|---|---|---|
| Agent 1 | Taxonomies & Frameworks | `taxonomies/` | Sonnet 4.6 | `pending` | 0 |
| Agent 2 | Company Case Studies | `company-cases/` | Sonnet 4.6 | `pending` | 0 |
| Agent 3a | IDE & Authoring Tools (L1–4) | `tools-protocols/ide/` | Sonnet 4.6 | `pending` | 0 |
| Agent 3b | Infrastructure & Protocol Tools (L5–8) | `tools-protocols/infra/` | Sonnet 4.6 | `pending` | 0 |
| Agent 4 | Orchestration Patterns | `orchestration-patterns/` | Sonnet 4.6 | `pending` | 0 |
| Agent 5 | Terminology Glossary | `terminology/` | Haiku 4.5 | `pending` | 0 |
