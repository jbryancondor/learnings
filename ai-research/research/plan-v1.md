# Generative AI Engineer — Deep Research Plan v1

**Created:** 2026-04-04
**Version:** 1 (preliminary research completed before agent spawn)
**Goal:** Build a comprehensive, state-of-the-art knowledge base to become a Generative AI Engineer.
**Seed article:** [The 8 Levels of Agentic Engineering](https://www.bassimeledath.com/blog/levels-of-agentic-engineering) — Bassim Eledath

---

## Research Folder Structure

```
research/
├── plan.md                          ← this file (strategy + index)
├── INDEX.md                         ← master index of all sources (auto-updated by agents)
├── taxonomies/                      ← Agent 1: maturity models & frameworks
│   └── <article-slug>.md
├── company-cases/                   ← Agent 2: company case studies
│   └── <company-slug>.md
├── tools-protocols/                 ← Agent 3: tools, MCP, SDD, harness
│   └── <tool-slug>.md
├── orchestration-patterns/          ← Agent 4: multi-agent patterns & architecture
│   └── <pattern-slug>.md
└── terminology/                     ← Agent 5: glossary of AI engineering terms
    └── <term>.md
```

### File schema (every research file)

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

## Reference: The 8 Levels of Agentic Engineering

| Level | Name | Core Idea |
|---|---|---|
| 1 | Tab Complete | Copilot-style autocomplete |
| 2 | Agent IDE | Cursor-style multi-file AI editing |
| 3 | Context Engineering | Token optimization, system prompts, memory |
| 4 | Compounding Engineering | Plan→Delegate→Assess→Codify loop, rules files |
| 5 | MCP & Skills | Model Context Protocol, tools, APIs, CI pipelines |
| 6 | Harness Engineering | Observability, feedback loops, backpressure, security |
| 7 | Background Agents | Async multi-worker orchestration |
| 8 | Autonomous Agent Teams | Agent-to-agent coordination, no human loop |

---

## Competing Maturity Models (discovered in preliminary research)

| Model | Author / Company | Levels | URL |
|---|---|---|---|
| 8 Levels of Agentic Engineering | Bassim Eledath | 8 | https://www.bassimeledath.com/blog/levels-of-agentic-engineering |
| Steve Yegge's Framework | Steve Yegge | 0 → custom orchestrators w/ 10+ agents | TBD — mentioned in Martin Fowler March 2026 |
| Agentic AI Maturity Model | Microsoft Copilot Studio | L100–L500 | https://learn.microsoft.com/en-us/microsoft-copilot-studio/guidance/maturity-model-overview |
| Crawl / Walk / Run / Scale | Nexocode / Dextralabs | L1–L4 | https://nexocode.com/blog/posts/the-agentic-ai-maturity-model-crawl-walk-run-scale/ |
| Gartner Agentic AI Maturity Roadmap | Gartner | 5 stages | https://www.gartner.com/en/documents/6825634 |

---

## Company Index (sources grouped by company)

### Spotify
> Evidence of Level 7 (Background Agents). Built "Honk" — background coding agent producing 1,500+ merged PRs.

| Title | Date | URL |
|---|---|---|
| 1,500+ PRs Later: Spotify's Journey with Background Coding Agent (Honk, Part 1) | Nov 2025 | https://engineering.atspotify.com/2025/11/spotifys-background-coding-agent-part-1 |
| Context Engineering for Background Coding Agents (Honk, Part 2) | Nov 2025 | https://engineering.atspotify.com/2025/11/context-engineering-background-coding-agents-part-2 |
| Predictable Results Through Strong Feedback Loops (Honk, Part 3) | Dec 2025 | https://engineering.atspotify.com/2025/12/feedback-loops-background-coding-agents-part-3 |
| Our Multi-Agent Architecture for Smarter Advertising | Feb 2026 | https://engineering.atspotify.com/2026/2/our-multi-agent-architecture-for-smarter-advertising |

### Martin Fowler / Thoughtworks
> Most comprehensive practitioner series on GenAI in software engineering (25 articles, 2023–2026). Focus on Q4 2025 and 2026 entries.

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

### Microsoft
> Agentic AI maturity model + AI-led SDLC with Azure and GitHub.

| Title | Date | URL |
|---|---|---|
| Agentic AI Adoption Maturity Model | 2025 | https://learn.microsoft.com/en-us/microsoft-copilot-studio/guidance/maturity-model-overview |
| An AI-led SDLC with Azure and GitHub | 2025 | https://techcommunity.microsoft.com/blog/appsonazureblog/an-ai-led-sdlc-building-an-end-to-end-agentic-software-development-lifecycle-wit/4491896 |

### GitHub
> GitHub Copilot evolution, Spec-Kit (open-source SDD tool).

| Title | Date | URL |
|---|---|---|
| GitHub Spec-Kit — spec-driven.md | 2025 | https://github.com/github/spec-kit/blob/main/spec-driven.md |

### Amazon / AWS
> Amazon Kiro — SDD-first IDE tool.

| Title | Date | URL |
|---|---|---|
| Amazon Kiro (SDD tool) | 2025 | TBD — search required |

### Anthropic
> 16-agent C compiler case, Claude Code patterns, CLAUDE.md / AGENTS.md.

| Title | Date | URL |
|---|---|---|
| Anthropic multi-agent compiler | TBD | TBD — search required |

### Gartner
> Industry analyst perspective — 80% of engineers need upskill by 2027.

| Title | Date | URL |
|---|---|---|
| Gartner: GenAI will require 80% of engineering workforce to upskill | Oct 2024 | https://www.gartner.com/en/newsroom/press-releases/2024-10-03-gartner-says-generative-ai-will-require-80-percent-of-engineering-workforce-to-upskill-through-2027 |
| Gartner Agentic AI Maturity Roadmap | 2025 | https://www.gartner.com/en/documents/6825634 |

### Google
> Addy Osmani (Chrome DevRel) — LLM coding workflow 2026.

| Title | Date | URL |
|---|---|---|
| My LLM coding workflow going into 2026 — Addy Osmani | Dec 2025 | https://addyosmani.com/blog/ai-coding-workflow/ |

### MIT Technology Review
> Year-in-review: vibe coding → context engineering shift.

| Title | Date | URL |
|---|---|---|
| From vibe coding to context engineering: 2025 in software development | Nov 2025 | https://www.technologyreview.com/2025/11/05/1127477/from-vibe-coding-to-context-engineering-2025-in-software-development/ |

### Newsletters / Independent Authors
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

## Agent Assignments

### Agent 1 — Agentic Taxonomies & Competing Frameworks
**Output folder:** `taxonomies/`
**Priority:** Q4 2025 and 2026 sources first.
**Mission:** Map, compare, and synthesize the 5+ competing agentic maturity models. Find which companies align to which level. Cover Steve Yegge's framework specifically (referenced in Martin Fowler March 2026 but URL unknown).

**Confirmed sources to process:**
- Bassim Eledath — 8 Levels (seed article)
- Martin Fowler — Fragments March 2026 (Supervisory Engineering, Yegge, Chad Fowler)
- Martin Fowler — Humans and Agents in Software Engineering Loops (Mar 2026)
- Microsoft — Agentic AI Maturity Model (L100–L500)
- Nexocode — Crawl/Walk/Run/Scale
- Gartner — Agentic AI Maturity Roadmap
- arxiv — AI Agents vs. Agentic AI: A Conceptual Taxonomy

**Key searches to run:**
- Steve Yegge agentic engineering framework levels 2025
- "compound AI systems" maturity model
- arxiv "agentic AI software engineering taxonomy 2025 2026"
- AI maturity model enterprise 2026 Forrester

---

### Agent 2 — Company Case Studies
**Output folder:** `company-cases/`
**Priority:** Q4 2025 and 2026 sources first.
**Mission:** Document real-world implementations by company. Spotify is the primary target (3-part Honk series). Also cover Anthropic, Microsoft, Google, GitHub/Amazon.

**Confirmed sources to process:**
- Spotify Honk Part 1 (Nov 2025)
- Spotify Honk Part 2 (Nov 2025)
- Spotify Honk Part 3 (Dec 2025)
- Spotify Multi-Agent Architecture for Advertising (Feb 2026)
- Addy Osmani — LLM coding workflow 2026 (Google Chrome DevRel)
- Microsoft — AI-led SDLC with Azure and GitHub
- Dawn Liphardt — Agentic Coding: Spotify's Lessons Learned
- Dept of Product — How Spotify uses AI Agents to manage tech debt

**Key searches to run:**
- Anthropic background agents multi-agent case study 2025 2026
- Cursor autonomous agents production 2025
- GitHub Copilot Workspace real usage report 2025 2026
- Netflix / Uber / Airbnb AI agents engineering blog 2025 2026
- LinkedIn engineering AI agents production 2025 2026

---

### Agent 3 — Tools & Protocols Landscape
**Output folder:** `tools-protocols/`
**Priority:** Q4 2025 and 2026 sources first.
**Mission:** Map all tools a Generative AI Engineer uses. Cover MCP, IDE tools, SDD tools, memory systems, CLAUDE.md/AGENTS.md patterns, harness tooling.

**Confirmed sources to process:**
- Martin Fowler #21 — SDD: Kiro, spec-kit, and Tessl (Oct 2025)
- Martin Fowler #23 — Context Engineering for Coding Agents (Feb 2026)
- Martin Fowler #24 — Harness Engineering — first thoughts (Feb 2026)
- GitHub Spec-Kit — spec-driven.md
- Thoughtworks — SDD blog post
- Amplifi Labs — Definitive Glossary (MCP, RAG, Tool Calling etc.)
- The New Stack — Memory for AI Agents (2025)
- Spotify Honk Part 2 — Context Engineering deep dive

**Key searches to run:**
- "Model Context Protocol MCP" tools ecosystem 2025 2026
- Claude Code CLAUDE.md AGENTS.md best practices
- Amazon Kiro SDD IDE 2025
- Tessl AI-first IDE 2025
- Cursor vs Windsurf vs Claude Code comparison 2026
- MemGPT Mem0 MemOS memory systems comparison 2025
- LLM observability tools LangSmith Langfuse 2025 2026
- Harness engineering AI agents tools

---

### Agent 4 — Orchestration & Background Agent Patterns
**Output folder:** `orchestration-patterns/`
**Priority:** Q4 2025 and 2026 sources first.
**Mission:** Deep dive into multi-agent architecture patterns, design patterns, and the concepts introduced by Martin Fowler's recent entries.

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

**Key searches to run:**
- LangGraph multi-agent 2025 2026 production patterns
- AutoGen Microsoft multi-agent framework 2025
- CrewAI orchestration patterns 2025
- "plan execute" agent pattern LLM 2025
- LLM as judge evaluation pattern 2025
- ReAct chain of thought agent patterns
- Background agent dispatcher pattern 2025

---

### Agent 5 — AI Terminology & Concepts Glossary
**Output folder:** `terminology/`
**Priority:** Cover all terms, especially those from Q4 2025 and 2026 articles.
**Mission:** Define every key term in the Generative AI Engineer vocabulary. One file per term. Discover new terms from the articles found by other agents.

**Full term list (v1 — 45 terms):**

_From user + seed article:_
- Vibe Coding
- Context Engineering
- AGENTS.md / CLAUDE.md
- Skills (MCP Skills)
- Memory Bank
- SDD (Spec-Driven Development)
- AI Fluency
- Agentic Engineering
- Background Agents
- Harness Engineering
- Backpressure (AI systems)
- MCP (Model Context Protocol)

_Discovered in preliminary research:_
- Supervisory Engineering
- Middle Loop
- Regenerative Architecture
- Evaluation over Review
- Autonomous Development Loop
- Multi-Model Systems
- MemOS
- Vibe Coding Hangover
- Compounding Engineering
- Anchoring to a Reference Application
- Spec-Kit (GitHub)
- Amazon Kiro
- Tessl

_Standard AI engineering vocabulary:_
- Prompt Engineering
- RAG (Retrieval-Augmented Generation)
- LLM-as-Judge
- Grounding
- Tool Use / Function Calling
- Few-shot / Zero-shot Prompting
- Chain of Thought (CoT)
- ReAct Pattern
- Compound AI Systems
- AI Pair Programming
- Orchestration
- System Prompt
- Temperature / Top-p
- Fine-tuning vs Prompting
- Hallucination
- Tokenization / Token Budget
- Embeddings
- Vector Database
- Context Window
- Agent Framework
- AI Alignment

**Key searches to run:**
- Each term individually to find the canonical source/definition
- LinkedIn articles for: AI fluency, compounding engineering, context engineering 2025
- swyx.io, Simon Willison blog for emerging terminology
- Andrej Karpathy vibe coding original post Feb 2025

---

## Technology Stack by Agentic Level

This section maps the tools, CLIs, editors, protocols, and frameworks you can adopt at each level. Organized so you can see exactly what to learn and install as you progress.

---

### Level 1 — Tab Complete
> Goal: AI-powered inline code suggestions inside your editor.

| Tool | Type | Adoptable? | Notes |
|---|---|---|---|
| GitHub Copilot | VS Code / JetBrains extension | ✅ Yes | Industry standard, $10/mo Pro plan |
| Tabnine | Extension (any IDE) | ✅ Yes | Privacy-first, runs locally |
| Codeium | Extension / standalone | ✅ Yes | Free tier, built into Windsurf |
| Amazon Q Developer | Extension | ✅ Yes | AWS-focused inline completions |

---

### Level 2 — Agent IDE
> Goal: Multi-file AI editing with chat, context awareness, and codebase indexing.

| Tool | Type | Adoptable? | Notes |
|---|---|---|---|
| **Cursor** | AI-first IDE (VS Code fork) | ✅ Yes | Largest community, `.cursorrules` support |
| **Windsurf** | AI-first IDE (Codeium) | ✅ Yes | Best price/feature ratio ($15/mo), Cascade agent |
| **GitHub Copilot Workspace** | Cloud IDE + agent | ✅ Yes | Tight GitHub integration, task-to-PR flow |
| **VS Code + Copilot Chat** | Extension on existing IDE | ✅ Yes | Lowest friction if already on VS Code |
| **JetBrains AI Assistant** | Plugin | ✅ Yes | Best for Java/Kotlin/Python ecosystems |
| **Google Antigravity** | Agentic IDE | ✅ Yes | True multi-agent orchestration + built-in browser for live testing (2025) |
| **Amazon Kiro** | Agentic IDE (SDD-first) | ✅ Yes | Spec-driven development + hooks system; only IDE with SDD built-in |

---

### Level 3 — Context Engineering
> Goal: Control what the AI sees. Optimize every token for accuracy and relevance.

| Tool | Type | Adoptable? | Notes |
|---|---|---|---|
| **CLAUDE.md** | Rules file (Claude Code) | ✅ Yes | Persistent instructions injected into every session |
| **AGENTS.md** | Rules file (any agent) | ✅ Yes | Agent-agnostic conventions file |
| **.cursorrules** | Rules file (Cursor) | ✅ Yes | Cursor-specific context rules |
| **.windsurfrules** | Rules file (Windsurf) | ✅ Yes | Windsurf-specific context rules |
| **Mem0** | Memory library | ✅ Yes | Persistent user/session memory for LLM apps |
| **MemGPT** | Memory agent framework | ✅ Yes | Long-term memory via virtual context management |
| **MemOS** | Memory OS for AI | 🔬 Research | arXiv 2025 — memory as a first-class OS layer |
| **Amazon Kiro hooks** | Automation hooks | ✅ Yes | Auto-trigger agent actions on file/event changes |

---

### Level 4 — Compounding Engineering
> Goal: Each AI session improves the next. Codify learnings into rules files automatically.

| Tool | Type | Adoptable? | Notes |
|---|---|---|---|
| **Claude Code** | CLI agent | ✅ Yes | Native CLAUDE.md loop; plan→delegate→assess→codify |
| **Cursor + rules** | IDE | ✅ Yes | `.cursorrules` updated after each session |
| **Amazon Kiro + specs** | IDE | ✅ Yes | Spec files evolve alongside the codebase |
| **GitHub Spec-Kit** | Open-source SDD tool | ✅ Yes | Places spec at the centre of the dev process |

---

### Level 5 — MCP & Skills
> Goal: Give the agent hands. Connect it to databases, APIs, CI pipelines, browsers.

| Tool | Type | Adoptable? | Notes |
|---|---|---|---|
| **MCP (Model Context Protocol)** | Open protocol | ✅ Yes | Standard by Anthropic (Nov 2024); 97M monthly SDK downloads as of Feb 2026 |
| **A2A (Agent-to-Agent Protocol)** | Open protocol | ✅ Yes | Google's complementary protocol for agent-to-agent communication; both now under Linux Foundation AAIF (Dec 2025) |
| **MCPM** | CLI package manager | ✅ Yes | `mcpm install <server>` — discovers, installs, configures MCP servers |
| **MCP Servers (official)** | Collection | ✅ Yes | github.com/modelcontextprotocol/servers — filesystem, GitHub, Slack, DB, browser |
| **Claude Code skills** | Custom skills | ✅ Yes | `.claude/skills/` — reusable agent behaviors triggered by slash commands |
| **fast-agent** | CLI framework | ✅ Yes | Creates sophisticated agents/workflows via CLI with MCP support |
| **PulseMCP** | MCP registry | ✅ Yes | pulsemcp.com — discover 546+ MCP clients and servers |

---

### Level 6 — Harness Engineering
> Goal: Build the environment around the agent — observability, feedback loops, guardrails.

| Tool | Type | Adoptable? | Notes |
|---|---|---|---|
| **LangSmith** | LLM observability | ✅ Yes | Tracing, evaluation, dataset management (LangChain) |
| **Langfuse** | LLM observability | ✅ Yes | Open-source alternative to LangSmith |
| **Helicone** | LLM proxy + observability | ✅ Yes | Drop-in proxy, logs all LLM calls |
| **Braintrust** | Eval platform | ✅ Yes | LLM-as-judge evaluations, CI integration |
| **Claude Code hooks** | Harness automation | ✅ Yes | Pre/post tool-call hooks in `settings.json` |
| **GitHub Actions / CI** | CI/CD | ✅ Yes | Automated feedback loop — agent opens PR, CI validates |
| **Gitleaks** | Secret scanning | ✅ Yes | Runs on every push; catches secrets before deploy |

---

### Level 7 — Background Agents
> Goal: Agents run async, without you watching. Orchestrate multiple workers across tasks.

| Tool | Type | Adoptable? | Notes |
|---|---|---|---|
| **Claude Code** (background mode) | CLI | ✅ Yes | Run headless, pipe output, spawn subagents |
| **OpenAI Codex CLI** | CLI agent | ✅ Yes | Background coding agent from OpenAI, desktop command center |
| **Dispatch** | Orchestrator tool | 🔬 Research | Bassim Eledath's internal tool — manages workers across different models |
| **Spotify Honk** | Internal agent | 📖 Reference | Spotify's background coding agent — 1,500+ PRs, not public but documented |
| **LangGraph** | Agent orchestration | ✅ Yes | State machine for multi-step agentic workflows |
| **Claude Agent SDK** | SDK | ✅ Yes | Security-first production agent orchestration |
| **OpenAI Agents SDK** | SDK | ✅ Yes | Delegation patterns, handoff between agents |

---

### Level 8 — Autonomous Agent Teams
> Goal: Agents coordinate directly. No central human loop. Frontier territory.

| Tool | Type | Adoptable? | Notes |
|---|---|---|---|
| **Google Antigravity** | Agentic IDE | ✅ Yes | Only consumer tool with true multi-agent orchestration today |
| **AutoGen (Microsoft)** | Framework | ✅ Yes | Multi-agent conversation framework; agents as actors |
| **CrewAI** | Framework | ✅ Yes | Role-based multi-agent crews with task delegation |
| **LangGraph** | Framework | ✅ Yes | Graph-based agent coordination, cycles, branching |
| **Claude Agent SDK** | SDK | ✅ Yes | Anthropic's production-grade agent orchestration |
| **A2A Protocol** | Protocol | ✅ Yes | Direct agent-to-agent communication standard |
| **mcp-agent** | Library | ✅ Yes | github.com/lastmile-ai/mcp-agent — build agents using MCP + workflow patterns |

---

### Protocols & Standards (cross-level)

| Protocol | Created by | Year | Purpose |
|---|---|---|---|
| **MCP** (Model Context Protocol) | Anthropic → Linux Foundation AAIF | Nov 2024 | Standard for connecting AI to tools, APIs, data sources |
| **A2A** (Agent-to-Agent) | Google → Linux Foundation AAIF | 2025 | Standard for direct agent-to-agent communication |

> Both MCP and A2A are now governed by the **Agentic AI Foundation (AAIF)** under the Linux Foundation, co-founded by: Anthropic, OpenAI, Google, Microsoft, AWS, Block (Dec 2025).

---

### Adoption Recommendation (for Generative AI Engineer role)

| Priority | Tool | Why |
|---|---|---|
| 🔴 Start now | Claude Code (CLI) | Native MCP, skills, CLAUDE.md loop — covers levels 3–7 |
| 🔴 Start now | Cursor or Windsurf | Agent IDE — covers levels 2–4 |
| 🔴 Start now | GitHub Copilot | Tab complete + Chat — covers levels 1–2 |
| 🟡 Learn next | MCP servers + MCPM | Unlocks level 5 — gives agents real tools |
| 🟡 Learn next | Amazon Kiro | SDD-first workflow — only IDE with spec + hooks built in |
| 🟡 Learn next | LangSmith or Langfuse | Observability — required for level 6 |
| 🟢 When ready | LangGraph / CrewAI | Multi-agent orchestration — levels 7–8 |
| 🟢 When ready | A2A Protocol | Direct agent coordination — level 8 |

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

## Success Criteria

- [ ] At least 30 source articles researched across all agents
- [ ] At least 45 terminology entries defined (one file each)
- [ ] Spotify Level 7 documented with all 4 primary sources
- [ ] All 5 competing maturity models compared in taxonomies/
- [ ] Steve Yegge's framework found and documented
- [ ] Martin Fowler Exploring GenAI #18–#25 all processed
- [ ] SDD tools (Kiro, Spec-Kit, Tessl) documented
- [ ] Company index in INDEX.md fully populated
- [ ] All files follow the standard schema
- [ ] Focus: 80%+ of sources from Q4 2025 or 2026

---

## Status

| Agent | Status | Files Created |
|---|---|---|
| Agent 1 — Taxonomies | `pending` | 0 |
| Agent 2 — Company Cases | `pending` | 0 |
| Agent 3 — Tools & Protocols | `pending` | 0 |
| Agent 4 — Orchestration Patterns | `pending` | 0 |
| Agent 5 — Terminology | `pending` | 0 |
