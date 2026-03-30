# 14 — Devika

## 1. Overview
The first open-source implementation of an Agentic Software Engineer — originally an alternative to Cognition AI's Devin. Understands high-level human instructions, breaks them into steps, researches information, and writes code. Uses specialized sub-agents for cognitive tasks.

## 2. Key Data

| Attribute | Value |
|---|---|
| **Maker** | Mufeed VH / Stition AI (Kerala, India) |
| **Type** | Open-source autonomous AI software engineer |
| **GitHub Stars** | ~19,500 |
| **Forks** | 2,600+ |
| **License** | MIT |
| **Launched** | March 2024 |
| **Spec Format** | Natural language instructions → agent decomposition |
| **SDD Level** | Autonomous (agent-driven spec creation) |
| **Agent Lock-in** | None — supports Claude 3, GPT-4, Gemini, Mistral, Groq, local LLMs via Ollama |
| **Languages** | Multi-language |
| **Pricing** | Free |

## 3. How It Works

### Architecture
Cognitive abilities powered by specialized sub-agents (Python classes). Agents communicate with LLMs through Jinja2 prompt templates.

### Workflow
1. Receive high-level instruction from human
2. Break down into implementation steps
3. Research relevant information (web browsing)
4. Write code to achieve the objective
5. Review and iterate

### Sub-Agents
- **Planner** — Breaks down tasks
- **Researcher** — Web search and information gathering
- **Coder** — Writes implementation code
- **Reviewer** — Checks code quality

## 4. Example Spec

### Input (Natural Language)
```
"Build a user registration API with email verification using Express.js,
PostgreSQL, and SendGrid. Include JWT authentication and rate limiting."
```

### Devika's Internal Decomposition
```
Step 1: Research best practices for Express.js auth APIs
Step 2: Set up project structure (Express + TypeScript)
Step 3: Create database schema (users, verification_tokens)
Step 4: Implement registration endpoint with bcrypt hashing
Step 5: Set up SendGrid email service
Step 6: Add email verification flow
Step 7: Implement JWT token issuance
Step 8: Add rate limiting middleware
Step 9: Write tests
Step 10: Create API documentation
```

## 5. Strengths
- Fully autonomous — minimal human intervention needed
- Supports many LLM backends (Claude, GPT-4, Gemini, local models)
- Web research capabilities (can gather context from the internet)
- MIT licensed — fully open source
- Large community (19.5K stars)
- No spec writing overhead — works from natural language

## 6. Weaknesses / Criticisms
- Early development/experimental stage — many unimplemented/broken features
- Less predictable than spec-driven tools (no formal spec guardrails)
- Can produce inconsistent results without structured specs
- No formal spec evolution or maintenance
- Autonomous approach may not suit teams needing review gates

## 7. Adoption & Community
- 19,500+ GitHub stars, 2,600+ forks
- One of the first open-source Devin alternatives
- International attention from India's tech community
- Active development with community contributions

## 8. When to Choose This Tool
- You want **full autonomy** with minimal human intervention
- You prefer **natural language** over structured specs
- You want **web research** capabilities baked in
- You use **local LLMs** (Ollama) or want multi-provider support
- You're comfortable with **experimental** tooling
- You want an open-source **Devin alternative**

## 9. Sources
- [GitHub Repository](https://github.com/stitionai/devika)
- [Architecture Docs](https://github.com/stitionai/devika/blob/main/ARCHITECTURE.md)
- [Devika AI Website](https://devikaai.co/)
- [SkyWork: Devika AI Guide](https://skywork.ai/skypage/en/devika-ai-guide-developers/1976904321982328832)
- [AgentHunt: Devika AI](https://agenthunt.io/agent/detail/github-com-stitionai-devika/)
- [KaliIO: Inside Devika](https://www.kaliio.com/unlocking-innovation-inside-devika-indias-open-source-ai-engineer-revolutionizing-software-development/)
