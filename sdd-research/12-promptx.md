# 12 — PromptX

## 1. Overview
An AI Agent Context Platform by Deepractice that uses natural language to create professional AI roles. Ships 8 built-in specialist roles. Available as MCP server. Accepted at WWW Companion '26 (academic paper). Characterized by "naturalness" vs other frameworks' depth or rigor.

## 2. Key Data

| Attribute | Value |
|---|---|
| **Maker** | Deepractice |
| **Type** | Open-source AI agent context platform |
| **License** | Open source |
| **Spec Format** | Natural language roles + context engineering |
| **SDD Level** | Role-based (natural language driven) |
| **Agent Lock-in** | None (MCP server) |
| **Install** | `npx -y @promptx/mcp-server` |
| **Languages** | Language-agnostic |
| **Pricing** | Free |
| **Academic** | Accepted at WWW Companion '26 |

## 3. How It Works

### Role-Based Approach
"One sentence, one expert." Activate any of 8 built-in specialist roles with a single message. Each role is a domain expert with specific capabilities.

### MCP Server
Available as MCP server — integrates with any MCP-compatible agent.

### Key Innovation
Natural language role assignment — no configuration files, YAML, or setup. Describe what you need and PromptX creates the expert.

### Academic Backing
Paper: "PromptX: A Cognitive Agent Platform with Long-term Memory" — accepted at WWW Companion '26.

## 4. Example Spec

### Activating a Role
```
"I need a backend architect who specializes in microservices and event-driven architecture"
```

### PromptX creates the role:
```markdown
# Role: Backend Architect

## Expertise
- Microservices architecture patterns
- Event-driven systems (Kafka, RabbitMQ)
- API design (REST, gRPC, GraphQL)
- Database selection and schema design
- Infrastructure as Code

## Behavior
- Always consider scalability and fault tolerance
- Recommend event sourcing for complex domains
- Prefer PostgreSQL for relational, Redis for caching
- Design APIs contract-first (OpenAPI spec before code)

## When Asked to Build User Registration:
1. Define the bounded context (Auth service)
2. Design events: UserRegistered, EmailVerified, LoginAttempted
3. Spec the API contract:
   - POST /auth/register → UserRegistered event
   - POST /auth/verify → EmailVerified event
4. Define data model with eventual consistency in mind
5. Recommend integration tests over unit tests for service boundaries
```

## 5. Strengths
- Most natural/intuitive SDD approach — just describe the expert you need
- Academic backing (WWW Companion '26)
- MCP server integration
- No configuration overhead
- 8 pre-built specialist roles
- Long-term memory capabilities

## 6. Weaknesses / Criticisms
- Less structured than dedicated spec frameworks
- Smaller community than Spec Kit, BMAD, or Superpowers
- Role-based approach may not provide enough guardrails
- Less documentation and examples available
- May feel too loose for teams wanting rigid process

## 7. Adoption & Community
- Academic recognition (WWW Companion '26)
- Compared alongside BMAD, spec-kit, and OpenSpec in formal analyses
- Characterized by "naturalness" in the SDD ecosystem
- Growing GitHub community

## 8. When to Choose This Tool
- You want the most **natural/intuitive** SDD approach
- You prefer **role-based** AI assistance over rigid workflows
- You want **MCP server** integration
- You value **academic rigor** (peer-reviewed approach)
- You want **minimal setup** — no YAML, no configuration files

## 9. Sources
- [GitHub Repository](https://github.com/Deepractice/PromptX)
- [Redreamality: BMAD vs spec-kit vs OpenSpec vs PromptX](https://redreamality.com/blog/-sddbmad-vs-spec-kit-vs-openspec-vs-promptx/)
- [spec-compare: 6 SDD Tools Compared](https://github.com/cameronsjo/spec-compare)
