# 02 — Amazon Kiro

## 1. Overview
AI-powered IDE by AWS that implements spec-driven development. A VS Code fork that takes developers from concept to production using structured specs with EARS notation, automated hooks, and deep AWS integration. Powered by Claude Sonnet.

## 2. Key Data

| Attribute | Value |
|---|---|
| **Maker** | Amazon Web Services (AWS) |
| **Type** | Standalone IDE (VS Code fork) |
| **GitHub Stars** | N/A (proprietary) |
| **License** | Proprietary |
| **Launched** | July 2025 |
| **Spec Format** | Markdown with EARS notation (`.kiro/specs/`) |
| **SDD Level** | Spec-first |
| **Agent Lock-in** | Yes — built-in agent (Claude Sonnet) |
| **Install** | Download from kiro.dev |
| **Languages** | Python, JavaScript (more planned) |
| **Pricing** | Free tier: 50 interactions/month |

## 3. How It Works

### Workflow
1. **Natural language prompt** — Describe what you want to build
2. **Requirements** — Kiro generates user stories with acceptance criteria in EARS notation
3. **Design doc** — Technical design with diagrams and schemas
4. **Task list** — Sequenced implementation tasks
5. **Implementation** — Agent executes tasks with human-in-the-loop approval

### Key Features
- **Agent Hooks** — Event-driven automation (e.g., on file save → run linter, security scan)
- **Agent Steering** — Persistent project context via `.kiro/steering/` markdown files
- **Multimodal Context** — Processes files, codebases, docs, images, terminal output via MCP
- **Kiro Autonomous Agent** — New frontier agent that works for hours/days

## 4. Example Spec

### Requirements (EARS notation)
```markdown
# Feature: User Authentication

## Requirement 1: User Registration
### User Story
As a new user, I want to register with my email and password
so that I can access the platform.

### Acceptance Criteria
- GIVEN a valid email and password
  WHEN the user submits the registration form
  THEN the system creates the account and sends a verification email

- GIVEN an email that already exists
  WHEN the user submits the registration form
  THEN the system returns a 409 Conflict error

- GIVEN a password shorter than 8 characters
  WHEN the user submits the registration form
  THEN the system returns a 400 Bad Request with validation errors

## Requirement 2: User Login
### User Story
As a registered user, I want to log in with my credentials.

### Acceptance Criteria
- GIVEN valid credentials
  WHEN the user submits the login form
  THEN the system returns a JWT access token (1h expiry)

- GIVEN 5 failed login attempts
  WHEN the user tries to log in again
  THEN the account is locked for 30 minutes
```

## 5. Strengths
- Integrated IDE experience — spec workflow built into the editor
- Agent Hooks provide powerful automation (CI-like behavior in the IDE)
- Agent Steering gives persistent project context
- Deep AWS service integration
- Backed by Amazon — enterprise support and longevity
- Free tier available
- EARS notation is a well-established requirements engineering format

## 6. Weaknesses / Criticisms
- "Like using a sledgehammer to crack a nut" for small bug fixes — Martin Fowler article
- Vendor lock-in (AWS ecosystem, Claude Sonnet only)
- Limited language support (Python, JavaScript only as of launch)
- Proprietary — can't extend or customize the SDD workflow
- No mention of how to use requirements in a spec-anchored way over time
- Only spec-first, not spec-anchored or spec-as-source

## 7. Adoption & Community
- Built by AWS — enterprise credibility
- Used in life sciences (drug discovery agents), automotive, manufacturing
- AWS re:Invent 2025 featured Kiro prominently
- Three frontier agents announced: Kiro autonomous agent, AWS Security Agent, AWS DevOps Agent
- Active development with new features planned for 2026

## 8. When to Choose This Tool
- Your team is **heavily invested in AWS** infrastructure
- You want an **integrated IDE** (not separate CLI tools)
- You prefer a **visual, guided** spec workflow
- You work primarily with **Python or JavaScript**
- You want **event-driven automation** (Agent Hooks)
- You're building **medium-to-large features** (not small bug fixes)

## 9. Sources
- [Official Website](https://kiro.dev/)
- [Kiro Docs: Specs](https://kiro.dev/docs/specs/)
- [InfoQ: AWS Kiro Spec-Driven Agent](https://www.infoq.com/news/2025/08/aws-kiro-spec-driven-agent/)
- [Martin Fowler: Understanding SDD](https://martinfowler.com/articles/exploring-gen-ai/sdd-3-tools.html)
- [Visual Studio Magazine: AWS's Kiro](https://visualstudiomagazine.com/articles/2025/07/21/forked-again-awss-kiro-latest-ai-assistant-based-on-vs-code.aspx)
- [OpenAI Tools Hub: Kiro Review](https://www.openaitoolshub.org/en/blog/kiro-review-amazon-ide)
- [Six Five Media: Spec-Driven Development with Kiro](https://www.sixfivemedia.com/content/from-prompt-to-production-ai-spec-driven-development-with-kiro---six-five-on-the-road)
- [AWS Blog: Drug Discovery Agent with Kiro](https://aws.amazon.com/blogs/industries/from-spec-to-production-a-three-week-drug-discovery-agent-using-kiro/)
- [Atal Upadhyay: SDD with Kiro on AWS](https://atalupadhyay.wordpress.com/2026/03/11/spec-driven-development-with-kiro-on-aws/)
