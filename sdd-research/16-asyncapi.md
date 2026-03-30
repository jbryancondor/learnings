# 16 — AsyncAPI

## 1. Overview
The OpenAPI equivalent for event-driven architectures. Provides a specification format for defining asynchronous APIs (message brokers, WebSockets, IoT). Includes code generation, documentation, and validation tools.

## 2. Key Data

| Attribute | Value |
|---|---|
| **Maker** | AsyncAPI Initiative (Linux Foundation) |
| **Type** | Open-source specification + tooling |
| **GitHub Stars** | ~4,000+ |
| **License** | Apache-2.0 |
| **Spec Format** | AsyncAPI YAML/JSON |
| **SDD Level** | API-first (event-driven contracts) |
| **Agent Lock-in** | N/A (not AI-based) |
| **Install** | `npm install -g @asyncapi/cli` |
| **Languages** | Multi-language code generation |
| **Pricing** | Free |

## 3. How It Works

### Workflow
1. Define async API in AsyncAPI format (YAML/JSON)
2. Validate spec: `asyncapi validate spec.yaml`
3. Generate code: `asyncapi generate fromTemplate spec.yaml <template>`
4. Generate documentation: `asyncapi generate fromTemplate spec.yaml @asyncapi/html-template`

### Covers
- Message brokers (Kafka, RabbitMQ, NATS, Pulsar)
- WebSockets
- MQTT (IoT)
- Server-Sent Events

## 4. Example Spec

### asyncapi.yaml
```yaml
asyncapi: 3.0.0
info:
  title: User Events Service
  version: 1.0.0
  description: User registration and verification events

channels:
  userRegistered:
    address: user/registered
    messages:
      UserRegisteredMessage:
        payload:
          type: object
          properties:
            userId:
              type: string
              format: uuid
            email:
              type: string
              format: email
            registeredAt:
              type: string
              format: date-time

  emailVerified:
    address: user/email-verified
    messages:
      EmailVerifiedMessage:
        payload:
          type: object
          properties:
            userId:
              type: string
              format: uuid
            verifiedAt:
              type: string
              format: date-time

operations:
  publishUserRegistered:
    action: send
    channel:
      $ref: '#/channels/userRegistered'
    summary: Publish when a new user registers

  onEmailVerified:
    action: receive
    channel:
      $ref: '#/channels/emailVerified'
    summary: Handle email verification events
```

## 5. Strengths
- Standard for event-driven API specs (like OpenAPI for REST)
- Linux Foundation backed — strong governance
- Code generation for multiple languages
- Interactive documentation
- Covers Kafka, RabbitMQ, MQTT, WebSockets

## 6. Weaknesses / Criticisms
- Smaller ecosystem than OpenAPI
- Only for event-driven/async APIs
- Not AI-powered
- Fewer code generation templates than OpenAPI Generator

## 7. Adoption & Community
- Linux Foundation project
- 4,000+ GitHub stars
- Growing adoption in event-driven microservices
- Standard companion to OpenAPI for async patterns

## 8. When to Choose This Tool
- You're building **event-driven** architectures
- You use **Kafka, RabbitMQ, MQTT, or WebSockets**
- You want **contract-first** development for async APIs
- You need **documentation** for message schemas
- You're combining with OpenAPI for a complete API spec strategy

## 9. Sources
- [Official Website](https://www.asyncapi.com/)
- [GitHub Repository](https://github.com/asyncapi/spec)
- [AsyncAPI CLI](https://github.com/asyncapi/cli)
- [AsyncAPI Docs](https://www.asyncapi.com/docs)
