# 13 — OpenAPI Generator

## 1. Overview
The most mature and widely-used spec-driven code generation tool. Write an OpenAPI specification, generate client SDKs, server stubs, and API documentation in 50+ programming languages. The de facto standard for API-first development. Not AI-powered — template-based generation.

## 2. Key Data

| Attribute | Value |
|---|---|
| **Maker** | OpenAPI Tools (community) |
| **Type** | Open-source CLI code generator |
| **GitHub Stars** | ~23,000 |
| **Contributors** | 3,500+ |
| **Forks** | 6,500+ |
| **License** | Apache-2.0 |
| **Spec Format** | OpenAPI 2.0/3.0/3.1 (YAML or JSON) |
| **SDD Level** | API-first (contract-driven) |
| **Agent Lock-in** | N/A (not AI-based) |
| **Install** | CLI, Maven/Gradle plugins, Docker, npm |
| **Languages** | 50+ targets |
| **Pricing** | Free |

## 3. How It Works

### Workflow
1. Write OpenAPI specification (YAML/JSON)
2. Run generator: `openapi-generator-cli generate -i spec.yaml -g <target> -o ./output`
3. Get generated client SDKs, server stubs, or documentation
4. Customize via templates (Mustache/Handlebars)

### Generation Targets (50+)
TypeScript, Java, Python, Go, Rust, C#, Ruby, Kotlin, Swift, PHP, Dart, Scala, and many more.

### Output Types
- **Client SDKs** — Ready-to-use API clients
- **Server stubs** — Skeleton implementations
- **Documentation** — Interactive API docs
- **Configuration** — Docker, CI/CD files

## 4. Example Spec

### OpenAPI 3.0 Specification
```yaml
openapi: 3.0.3
info:
  title: User API
  version: 1.0.0
  description: User management service

paths:
  /users:
    post:
      summary: Register a new user
      operationId: createUser
      requestBody:
        required: true
        content:
          application/json:
            schema:
              $ref: '#/components/schemas/CreateUserRequest'
      responses:
        '201':
          description: User created
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/User'
        '409':
          description: Email already exists

  /users/{id}:
    get:
      summary: Get user by ID
      operationId: getUser
      parameters:
        - name: id
          in: path
          required: true
          schema:
            type: string
            format: uuid
      responses:
        '200':
          description: User found
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/User'
        '404':
          description: User not found

components:
  schemas:
    CreateUserRequest:
      type: object
      required: [email, password]
      properties:
        email:
          type: string
          format: email
        password:
          type: string
          minLength: 8
    User:
      type: object
      properties:
        id:
          type: string
          format: uuid
        email:
          type: string
          format: email
        created_at:
          type: string
          format: date-time
```

### Generate TypeScript Client
```bash
openapi-generator-cli generate \
  -i spec.yaml \
  -g typescript-axios \
  -o ./client \
  --additional-properties=npmName=user-api-client
```

### Generated Code (TypeScript)
```typescript
// Auto-generated — do not edit
export interface CreateUserRequest {
  email: string;
  password: string;
}

export interface User {
  id?: string;
  email?: string;
  created_at?: string;
}

export class DefaultApi {
  async createUser(request: CreateUserRequest): Promise<User> { ... }
  async getUser(id: string): Promise<User> { ... }
}
```

## 5. Strengths
- Most mature SDD tool (6+ years, 23K stars)
- 50+ language targets — unmatched breadth
- 3,500+ contributors — massive community
- Custom templates for full control
- No AI dependency — deterministic output
- Industry standard for API-first development
- Used by Google, Microsoft, IBM, Stripe, Twilio, Spotify

## 6. Weaknesses / Criticisms
- Not AI-powered — template-based (less flexible)
- Generated code can be verbose or non-idiomatic
- Only works for API contracts (not general SDD)
- Requires learning OpenAPI spec format
- Custom templates have a learning curve
- Multiple releases per month can cause breaking changes

## 7. Adoption & Community
- Universal adoption — from startups to FAANG
- Google, Microsoft, IBM, Stripe, Twilio, Spotify all use it
- Spotify's Web API documented with OpenAPI 3.0 (machine-readable for AI tools)
- De facto standard for API-first development
- Active maintenance with multiple monthly releases

## 8. When to Choose This Tool
- You're building **REST APIs** and want contract-first development
- You need **client SDKs** in multiple languages from one spec
- You want **deterministic** code generation (no AI variability)
- You're doing **API-first** development (not full SDD)
- You need the **broadest language support** (50+)
- You want **industry-standard** tooling

## 9. Sources
- [GitHub Repository](https://github.com/OpenAPITools/openapi-generator)
- [Official Website](https://openapi-generator.tech/)
- [Swagger/OpenAPI](https://swagger.io/)
- [Swagger UI (~27K stars)](https://github.com/swagger-api/swagger-ui)
- [Swagger Codegen (~17K stars)](https://github.com/swagger-api/swagger-codegen)
- [Spotify Developer: Building with AI](https://developer.spotify.com/documentation/web-api/tutorials/building-with-ai)
