# HCP-0009

# Reference HTTP API

Version: 0.4 (Draft)

Status: Draft

Category: Reference Specification

Project: Human Connection Network (HCN)

License: Apache-2.0

Last Updated: 2026-07-13

Depends On:

- HCP-0000 — Architecture and Overview
- HCP-0001 — Humanitarian Record
- HCP-0002 — HCP Node
- HCP-0005 — Node Communication Protocol
- HCP-0010 — Canonical JSON
- HCP-0011 — Query Model

Replaces:
None

Replaced By:
None

---

# Abstract

This document defines the recommended HTTP reference binding for the Humanitarian Connection Protocol (HCP).

It describes one possible HTTP interface through which HCP Clients and HCP Nodes may interact with an implementation of the protocol.

This document is **not part of the HCP Core semantics**.

Compatible implementations remain fully interoperable when exposing equivalent semantic behavior through different communication technologies.

The protocol standardizes humanitarian meaning.

This specification demonstrates one recommended way to expose that meaning through HTTP.

---

# 1. Introduction

The Humanitarian Connection Protocol defines semantic interoperability between independent humanitarian implementations.

HCP-0005 defines the conceptual communication model between HCP Nodes.

This specification defines one recommended HTTP binding implementing that communication model.

The HTTP API allows Clients and other Nodes to interact with an HCP implementation using widely adopted web technologies.

Although every example in this specification uses HTTP, the protocol itself remains completely transport-independent.

Equivalent implementations may expose identical semantic behavior through:

- gRPC;
- MQTT;
- Message Queues;
- Mesh Networks;
- SMS Gateways;
- Satellite Networks;
- Local APIs;
- future communication technologies.

Changing the transport never changes humanitarian meaning.

---

# 2. Purpose

The purpose of this specification is to define a recommended HTTP interface exposing the semantic capabilities of an HCP Node.

The API demonstrates how an implementation may expose operations such as:

- submit Humanitarian Records;
- query Humanitarian Records;
- synchronize Humanitarian Records;
- retrieve operational information.

The API intentionally remains minimal.

Implementations remain free to extend it according to their operational needs while preserving HCP semantic compatibility.

---

# 3. Design Principles

Every compatible HTTP implementation should preserve the following principles.

## Semantic

The API exposes HCP semantic concepts.

It never exposes implementation-specific behavior.

---

## Stateless

Every request should be processed independently.

Servers should not require conversational state between requests.

---

## Canonical

Every exchanged Humanitarian Record shall follow the Canonical JSON representation defined in **HCP-0010**.

---

## Language Independent

Clients may be implemented using any programming language.

HTTP remains only one possible transport.

---

## Extensible

Future HTTP operations may be introduced without affecting semantic interoperability.

---

## Transport Independent

HTTP is a reference transport.

The protocol itself remains transport-independent.

---

# 4. Reference HTTP Binding

The HTTP interface defined by this specification is a reference implementation.

Equivalent semantic behavior may be exposed through completely different communication technologies.

Examples include:

- REST APIs;
- gRPC services;
- Message Queues;
- MQTT brokers;
- Mesh synchronization;
- Local IPC;
- Future communication mechanisms.

Implementations remain compliant as long as they preserve the semantic behavior defined by HCP.

The protocol standardizes semantics.

The HTTP API standardizes one recommended HTTP binding.

---

# 5. Reference Endpoints

A reference HTTP implementation should expose operations conceptually equivalent to the following.

| Method | Endpoint | Purpose |
|---------|-----------|-----------------------------------------|
| POST | `/records` | Submit a Humanitarian Record |
| POST | `/query` | Query Humanitarian Records |
| POST | `/sync` | Synchronize Humanitarian Records |
| GET | `/health` | Retrieve operational information |

These endpoints are recommendations.

Equivalent interfaces may expose the same semantic behavior using different endpoint names or communication mechanisms.

---

# 6. Submit Humanitarian Record

A Client submits humanitarian information to an HCP Node.

The submitted payload shall follow the Canonical JSON Representation defined by **HCP-0010**.

Illustrative request:

```http
POST /records
```

Illustrative request body:

```json
{
  "subject": "human",
  "event_type": "missing_report",
  "reported_label": "Juan Pérez",
  "estimated_age": 42,
  "recognition_features": "Blue jacket, black backpack",
  "reported_location": "Caracas",
  "reported_by": "family"
}
```

Illustrative successful response:

```http
201 Created
```

```json
{
  "record_id": "2d36d31d-c987-4c35-b0a8-74cb8eb9b62e",
  "status": "created",
  "created_at": "2026-07-13T16:30:00Z"
}
```

The HTTP API receives a canonical Humanitarian Record.

The HCP Node validates it and stores it according to its local implementation.
---
# 7. Query Humanitarian Records

An HCP Client may query Humanitarian Records exposed by an HCP Node.

The submitted query shall follow the Query Model defined in **HCP-0011**.

Illustrative request:

```http
POST /query
```

Illustrative request body:

```json
{
  "subject": "human",
  "event_type": "missing_report",
  "reported_label": "Juan Pérez",
  "estimated_age": 42,
  "recognition_features": "Blue jacket",
  "reported_location": "Caracas"
}
```

The Node evaluates its locally available Humanitarian Records.

Correlation remains entirely implementation-specific.

Illustrative response:

```json
{
  "results": [
    {
      "record_id": "d71b5f...",
      "score": 0.93,
      "event_type": "hospital_admission",
      "explanation": [
        "Reported Labels are compatible",
        "Recognition Features are compatible",
        "Reported locations are compatible"
      ]
    }
  ]
}
```

The API standardizes request and response semantics.

It does not standardize correlation algorithms.

---

# 8. Synchronize Humanitarian Records

Independent HCP Nodes may synchronize Humanitarian Records through an HTTP interface.

Illustrative request:

```http
POST /sync
```

Illustrative request body:

```json
{
  "records": [
    {
      "...": "Canonical HCP JSON Representation"
    }
  ]
}
```

Illustrative response:

```http
202 Accepted
```

```json
{
  "accepted": 12,
  "rejected": 0
}
```

Synchronization behavior is defined by **HCP-0013 — Synchronization Model**.

This specification defines only one possible HTTP binding.

---

# 9. Operational Endpoints

Reference implementations may expose operational endpoints supporting administration and monitoring.

Illustrative example:

```http
GET /health
```

Illustrative response:

```json
{
  "status": "ok",
  "hcp_version": "0.4",
  "implementation_version": "1.2.0"
}
```

Operational endpoints are not part of humanitarian interoperability.

They exist exclusively to support implementation management.

Equivalent operational information may be exposed through different mechanisms.

---

# 10. Error Handling

Whenever possible, HTTP implementations should return structured machine-readable error responses.

Illustrative example:

```http
400 Bad Request
```

```json
{
  "error": "invalid_query",
  "message": "reported_label must be a string"
}
```

The exact error schema remains implementation-specific.

Implementations should avoid exposing unnecessary internal implementation details.

---

# 11. Authentication

Authentication and authorization remain outside the scope of HCP.

Different implementations may adopt authentication mechanisms appropriate to their operational environments.

Examples include:

- API Keys;
- OAuth 2.0;
- Mutual TLS;
- JWT;
- Internal Network Authentication;
- future authentication technologies.

Authentication mechanisms never affect protocol semantics.

---

# 12. Relationship with Other Specifications

This document defines one recommended HTTP binding for HCP.

It complements the semantic specifications defined throughout the HCP Core.

```text
HCP-0005
Node Communication Protocol
        │
        ▼
HCP-0009
Reference HTTP API
        │
        ▼
HTTP Interface
        │
        ▼
HCP Implementation
```

Each specification has a distinct responsibility.

- **HCP-0005** defines the semantic communication model.
- **HCP-0009** defines one recommended HTTP implementation of that model.
- **HCP-0010** defines the Canonical JSON representation.
- **HCP-0011** defines the Query Model.
- **HCP-0013** defines synchronization behavior.

Together, these specifications demonstrate how HCP semantics may be exposed through HTTP while preserving complete implementation independence.

---

# 13. Summary

The Reference HTTP API defines one recommended HTTP binding for the Humanitarian Connection Protocol.

It is not the protocol itself.

It is not the only valid implementation.

The protocol standardizes humanitarian semantics.

The Node Communication Protocol standardizes semantic communication.

This specification demonstrates one recommended HTTP interface exposing those semantics.

Equivalent behavior may be implemented using any transport technology while preserving interoperability.

Clients submit Humanitarian Records.

Nodes exchange Humanitarian Records.

Correlation remains local.

Humanitarian Cases remain local.

People verify reality.

By separating protocol semantics from transport technologies, HCP enables independent organizations to build interoperable humanitarian systems without requiring common software architectures, centralized databases or mandatory communication technologies.

The protocol standardizes semantics.

The communication model standardizes interaction.

The Reference HTTP API standardizes one recommended HTTP binding.

Implementations remain free.
