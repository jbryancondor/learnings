---
source: Synthesis of multiple frameworks
date_accessed: 2026-04-04
published: 2026-04-04
author: Agent-1 synthesis
company: Multiple
level_mapping: [1, 2, 3, 4, 5, 6, 7, 8]
tags: [taxonomy, synthesis, comparison, maturity-model, cross-framework-analysis]
agent: agent-1
---

## Summary

This file maps 7 competing agentic AI maturity frameworks side-by-side, analyzing where they agree, disagree, and how they map to the anchor framework: Bassim Eledath's 8 Levels of Agentic Engineering.

## The 7 Frameworks Compared

| # | Framework | Author/Org | Levels | Lens | Audience |
|---|-----------|-----------|--------|------|----------|
| 1 | 8 Levels of Agentic Engineering | Bassim Eledath | 8 | Skill & capability | Individual engineers |
| 2 | Developer-Agent Evolution | Steve Yegge | 8 | Trust & autonomy | Individual developers |
| 3 | Humans & Agents Spectrum | Kief Morris / Thoughtworks | 3 positions | Human-agent relationship | Engineering orgs |
| 4 | Copilot Studio Maturity Model | Microsoft | 5 (L100–L500) | Organizational readiness | Enterprise leaders |
| 5 | Crawl/Walk/Run/Scale | Nexocode | 4 | Implementation complexity | Enterprise practitioners |
| 6 | Agentic AI Maturity Roadmap | Gartner | 5 | Strategic capability | C-suite / analysts |
| 7 | AI Agents vs. Agentic AI | Sapkota et al. (arXiv) | 4 tiers | Architectural taxonomy | Researchers / architects |

---

## Cross-Framework Mapping to the 8 Levels

| 8 Levels (Eledath) | Yegge Stage | Morris Position | Microsoft | Nexocode | Gartner | arXiv Tier |
|---|---|---|---|---|---|---|
| **L1: Tab Complete** | S1: Zero/Near-Zero AI | — | L100: Initial | — | Awareness | Generative AI |
| **L2: Agent IDE** | S2: IDE + Permissions | In the Loop | L100–L200 | Crawl | Active | Generative AI |
| **L3: Context Engineering** | S3: IDE YOLO | In the Loop | L200 | Crawl–Walk | Active | AI Agents |
| **L4: Compounding Engineering** | S4: Wide Agent IDE | In → On the Loop | L200–L300 | Walk | Operational | AI Agents |
| **L5: MCP & Skills** | S5: CLI Single Agent | On the Loop | L300 | Walk–Run | Operational | AI Agents |
| **L6: Harness Engineering** | S5–S6: CLI YOLO | On the Loop (Harness) | L300–L400 | Run | Systemic | Agentic AI |
| **L7: Background Agents** | S6–S7: Multi-Agent | On the Loop (Flywheel) | L400 | Run–Scale | Advanced | Agentic AI |
| **L8: Autonomous Teams** | S8: Custom Orchestrator | Agentic Flywheel | L500 | Scale | Expert/Transformational | Agentic AI |

---

## Where the Frameworks Agree

### 1. Universal Progression Pattern

All frameworks describe the same fundamental arc:
**Passive assistance → Active tooling → Autonomous execution → Multi-agent orchestration**

Whether expressed as Crawl/Walk/Run/Scale, L100–L500, or Levels 1–8, every framework recognizes that maturity is a gradual shift from human-doing-the-work to human-governing-the-system.

### 2. The "Governance Inflection Point"

Every framework identifies a critical transition point where governance becomes mandatory:
- Eledath: Level 5–6 (MCP → Harness Engineering)
- Microsoft: L300 (Defined — formal governance emerges)
- Nexocode: Walk → Run (human intervention triggers required)
- Gartner: Operational → Systemic
- Forrester data: 50% piloting but only 24% in production — the governance gap

**Consensus**: You can experiment without governance, but you cannot scale without it.

### 3. The "Human Role Shift"

All frameworks agree that the human role transforms, not disappears:
- Morris: Outside → In → **On** the Loop
- Eledath: Coding → Reviewing → **Harness Engineering**
- Yegge: Approving → Reviewing diffs → **Orchestrating**
- Microsoft: Individual pilots → **Enterprise operating model**
- arXiv: Using tools → **Coordinating agents**

**Consensus**: The job becomes designing systems that govern AI, not doing the AI's work.

### 4. Multi-Agent as the Frontier

Every framework places multi-agent coordination at the most advanced stage:
- Eledath L8, Yegge S7–S8, Microsoft L500, Nexocode Scale, Gartner Expert, arXiv Agentic AI

**Consensus**: Multi-agent orchestration is where all roads lead, but it's still experimental and risky.

---

## Where the Frameworks Disagree

### 1. Individual vs. Organizational Unit of Analysis

| Individual-focused | Organization-focused |
|---|---|
| Eledath (engineer skills) | Microsoft (enterprise pillars) |
| Yegge (developer trust) | Nexocode (org infrastructure) |
| | Gartner (strategic capability) |

**Tension**: An individual engineer at Eledath Level 6 in an organization at Microsoft L100 will be frustrated and constrained. The frameworks measure different things — both are needed.

### 2. Trust vs. Skill as the Progression Axis

- **Yegge**: Progression is primarily about trust — turning off permissions, accepting YOLO mode
- **Eledath**: Progression is about skill — learning context engineering, building harnesses
- **Morris**: Progression is about relationship design — choosing the right loop position

**Implication**: These are three independent dimensions. You can trust agents (Yegge S5) without having the skill to build proper harnesses (Eledath L6), creating a dangerous gap.

### 3. Number of Stages

| Framework | Stages | Granularity |
|-----------|--------|-------------|
| Eledath | 8 | Fine-grained, each level is a distinct skill |
| Yegge | 8 | Fine-grained, each level is a trust threshold |
| Morris | 3 | Coarse — positional, not progressive |
| Microsoft | 5 | Medium — organizational assessment |
| Nexocode | 4 | Medium — implementation complexity |
| Gartner | 5 | Medium — strategic capability |
| arXiv | 4 | Coarse — architectural taxonomy |

**Implication**: The 8-level models are better for individual skill planning; the 4–5-level models are better for organizational assessment and communication with leadership.

### 4. The "Governance First" vs. "Governance Emergent" Debate

- **Microsoft & Gartner**: Governance must be established early (L200–L300) before scaling
- **Eledath & Yegge**: Governance (harness engineering) emerges naturally at Level 5–6 as agents become more capable
- **Forrester data**: Validates Microsoft/Gartner — organizations that skip governance get stuck in "perpetual pilot"

**Winner**: The enterprise frameworks are empirically correct. Governance should precede scaling, not follow it.

---

## Synthesis: A Unified 4-Phase Model

Collapsing all frameworks into their natural break points reveals **4 meta-phases**:

### Phase 1: Assisted (Levels 1–2)
AI as tool. Human does the work, AI helps at margins.
- Eledath: Tab Complete, Agent IDE
- Yegge: Zero AI, IDE + Permissions
- Nexocode: Crawl
- Microsoft: L100

### Phase 2: Augmented (Levels 3–5)
AI as partner. Human directs, AI executes tasks.
- Eledath: Context Engineering, Compounding, MCP & Skills
- Yegge: IDE YOLO, Wide Agent, CLI Single
- Morris: In the Loop → On the Loop transition
- Nexocode: Walk
- Microsoft: L200–L300

### Phase 3: Orchestrated (Level 6–7)
AI as workforce. Human designs systems, AI operates within them.
- Eledath: Harness Engineering, Background Agents
- Yegge: CLI Multi-Agent, 10+ Agents
- Morris: On the Loop + Agentic Flywheel
- Nexocode: Run
- Microsoft: L400

### Phase 4: Autonomous (Level 8)
AI as ecosystem. Agents coordinate with minimal human governance.
- Eledath: Autonomous Agent Teams
- Yegge: Custom Orchestrator
- Nexocode: Scale
- Microsoft: L500
- Gartner: Expert Autonomous Systems

---

## Key Gaps Across All Frameworks

1. **Security & adversarial robustness** — No framework adequately addresses agent-to-agent attack surfaces or prompt injection risks at scale
2. **Cost modeling** — Only Forrester touches ROI; no framework maps compute/token costs per maturity level
3. **Regression & rollback** — Eledath notes regression challenges at Level 8 but no framework provides systematic rollback patterns
4. **Team dynamics** — Only Eledath's "multiplayer effect" and the AI-MM SET role-based model address team-level adoption patterns
5. **Regulatory compliance** — Microsoft touches governance but no framework maps to specific regulatory frameworks (EU AI Act, etc.)

---

## Relevance to Generative AI Engineer Role

**Use Eledath's 8 Levels** for personal skill development — it's the most granular and practitioner-relevant.

**Use Yegge's model** as a trust self-assessment — where are you on the autonomy spectrum?

**Use Morris's framework** for the conceptual "aha" — the job is building the harness, not reviewing code.

**Use Microsoft/Gartner** when communicating with leadership — speak their language.

**Use Nexocode** when scoping projects — Crawl/Walk/Run/Scale is intuitive for stakeholders.

**Use the arXiv taxonomy** for architectural decisions — single agent vs. multi-agent is the key design choice.

**Use Forrester data** for reality checks — most orgs are earlier than they think they are.
