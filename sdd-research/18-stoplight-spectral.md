# 18 — Stoplight (Spectral + Prism)

## 1. Overview
A collaborative API design-first platform with open-source tools for linting (Spectral) and mocking (Prism) from OpenAPI specs. Acquired by SmartBear in 2023. Focuses on API governance, documentation, and design — not code generation. The "quality gate" for API specs.

## 2. Key Data

| Attribute | Value |
|---|---|
| **Maker** | Stoplight (acquired by SmartBear, 2023) |
| **Type** | Platform + open-source tools |
| **GitHub Stars** | Spectral: ~2,500; Prism: ~4,200; Elements: ~1,700 |
| **License** | Open-source tools: Apache-2.0; Platform: proprietary |
| **Spec Format** | OpenAPI 2.0/3.0/3.1, JSON Schema |
| **SDD Level** | API governance (design-first) |
| **Agent Lock-in** | N/A (not AI-based) |
| **Install** | `npm install -g @stoplight/spectral-cli` / `npm install -g @stoplight/prism-cli` |
| **Languages** | N/A (spec validation, not code generation) |
| **Pricing** | Tools: free; Platform: freemium + enterprise |

## 3. How It Works

### Spectral (API Linting)
Customizable API linting rules / style guides. Enforces consistency and best practices across your OpenAPI specs.

### Prism (API Mocking)
Generates a mock server automatically from your OpenAPI spec. Front-end teams can develop against the mock while back-end builds the real API.

### Platform
Visual OpenAPI editor, hosted documentation, Git integration, design review workflows.

## 4. Example Spec

### .spectral.yaml (API Style Guide)
```yaml
extends: spectral:oas
rules:
  operation-operationId:
    severity: error
    description: Every operation must have an operationId
  path-keys-no-trailing-slash:
    severity: warn
  info-contact:
    severity: error
    description: API must have contact information
  operation-description:
    severity: warn
    description: Each operation should have a description
  oas3-valid-schema-example:
    severity: error
  # Custom rules
  must-have-pagination:
    given: "$.paths.*.get.responses.200.content.application/json.schema"
    then:
      field: properties.pagination
      function: truthy
    severity: warn
    description: GET endpoints returning lists should support pagination
```

### Running Spectral
```bash
spectral lint spec.yaml

# Output:
# /spec.yaml
#  3:6  error  info-contact  API must have contact information
# 15:8  warn   operation-description  Each operation should have a description
#
# ✖ 2 problems (1 error, 1 warning)
```

### Running Prism (Mock Server)
```bash
prism mock spec.yaml
# Mock server running at http://127.0.0.1:4010

# Test:
curl http://localhost:4010/users -X POST \
  -H "Content-Type: application/json" \
  -d '{"email":"test@example.com","password":"SecurePass1"}'
# Returns mock response based on spec examples/schemas
```

## 5. Strengths
- Best-in-class API linting (Spectral)
- Automatic mock servers from specs (Prism)
- Custom linting rules for organizational standards
- Git integration (works with existing repos)
- Visual editor for non-technical users
- Open-source core tools
- Backed by SmartBear (enterprise support)

## 6. Weaknesses / Criticisms
- Not a code generator (delegates to OpenAPI Generator)
- Platform is proprietary (open-source tools are limited)
- Only for OpenAPI specs (not general SDD)
- Not AI-powered

## 7. Adoption & Community
- Used by Zoom, EA, SendGrid, Shopgate
- Spectral: 2,500+ stars; Prism: 4,200+ stars
- Bundled with SwaggerHub after SmartBear acquisition
- Standard in enterprise API governance

## 8. When to Choose This Tool
- You need **API governance** (linting, style guides)
- You want **mock servers** from specs for parallel front/back development
- You use **OpenAPI** specs and need quality gates
- You want **visual editing** for API design
- You need **enterprise** API governance tools

## 9. Sources
- [Stoplight Website](https://stoplight.io/)
- [Spectral GitHub](https://github.com/stoplightio/spectral)
- [Prism GitHub](https://github.com/stoplightio/prism)
- [Elements GitHub](https://github.com/stoplightio/elements)
- [Spectral Docs](https://docs.stoplight.io/docs/spectral/)
