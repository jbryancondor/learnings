# 15 — Buf (Protocol Buffers Ecosystem)

## 1. Overview
A modern developer tool for Protocol Buffers (Protobuf) ecosystem. Provides linting, breaking change detection, code generation, and a schema registry for Protobuf-first API development. The spec-driven tool of choice for gRPC teams.

## 2. Key Data

| Attribute | Value |
|---|---|
| **Maker** | Buf Technologies |
| **Type** | Open-source CLI + commercial registry |
| **GitHub Stars** | ~10,000+ |
| **License** | Apache-2.0 (CLI); commercial (BSR) |
| **Spec Format** | Protocol Buffers (.proto files) |
| **SDD Level** | API-first (contract-driven) |
| **Agent Lock-in** | N/A (not AI-based) |
| **Install** | `brew install bufbuild/buf/buf` or npm/Go/etc. |
| **Languages** | All Protobuf-supported languages |
| **Pricing** | Free CLI; Buf Schema Registry has paid tiers |

## 3. How It Works

### Workflow
1. Define APIs in `.proto` files (Protocol Buffers)
2. Lint with `buf lint` (consistent style)
3. Check for breaking changes: `buf breaking`
4. Generate code: `buf generate` (clients, servers, docs)
5. Publish to Buf Schema Registry (BSR) for sharing

### Key Features
- **Linting** — Enforce Protobuf style standards
- **Breaking Change Detection** — Catch API-breaking changes before merge
- **Code Generation** — Generate stubs in any Protobuf-supported language
- **Schema Registry (BSR)** — Share and version Protobuf schemas

## 4. Example Spec

### user.proto
```protobuf
syntax = "proto3";

package user.v1;

service UserService {
  rpc CreateUser(CreateUserRequest) returns (CreateUserResponse);
  rpc GetUser(GetUserRequest) returns (GetUserResponse);
  rpc VerifyEmail(VerifyEmailRequest) returns (VerifyEmailResponse);
}

message CreateUserRequest {
  string email = 1;
  string password = 2;
}

message CreateUserResponse {
  User user = 1;
}

message GetUserRequest {
  string id = 1;
}

message GetUserResponse {
  User user = 1;
}

message VerifyEmailRequest {
  string token = 1;
}

message VerifyEmailResponse {
  bool success = 1;
}

message User {
  string id = 1;
  string email = 2;
  google.protobuf.Timestamp created_at = 3;
  bool verified = 4;
}
```

### buf.yaml
```yaml
version: v2
modules:
  - path: proto
lint:
  use:
    - DEFAULT
breaking:
  use:
    - FILE
```

### Generate Code
```bash
buf generate
# Outputs: Go server stubs, TypeScript client, Python client, etc.
```

## 5. Strengths
- Best-in-class Protobuf tooling
- Breaking change detection prevents API regressions
- Schema Registry for versioning and sharing
- Deterministic code generation
- Works with any Protobuf-supported language
- Strong for microservices architectures

## 6. Weaknesses / Criticisms
- Only for Protobuf/gRPC (not REST or general SDD)
- Not AI-powered (template-based generation)
- Learning curve for teams new to Protobuf
- Commercial registry for advanced features

## 7. Adoption & Community
- 10,000+ GitHub stars
- Widely adopted in microservices-heavy organizations
- Standard tool for gRPC-first development
- Used alongside or as alternative to hand-written proto tooling

## 8. When to Choose This Tool
- You're building **gRPC/Protobuf** APIs
- You need **breaking change detection** for API contracts
- You want a **schema registry** for shared API definitions
- You're doing **microservices** architecture
- You need **deterministic** code generation from contracts

## 9. Sources
- [Official Website](https://buf.build/)
- [GitHub: buf](https://github.com/bufbuild/buf)
- [Buf Docs](https://buf.build/docs/)
- [Buf Schema Registry](https://buf.build/product/bsr)
