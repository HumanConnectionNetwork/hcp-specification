# HCP-0009
# Node API

Version: 0.2 (Draft)

Status: Draft

Category: Reference Specification

Authors: Human Connection Network Foundation

License: Apache-2.0

Last Updated: 2026-07-07

Depends On:

- HCP-0001 Humanitarian Record
- HCP-0005 Node Communication Protocol
- HCP-0010 Canonical JSON Specification
- HCP-0011 Query Model

---

# 1. Introduction

This document defines the recommended API exposed by an HCP Node.

The Node API provides a standardized interface through which applications, bots, mobile clients, hospital systems and other HCP Nodes can interact with an implementation of the Humanitarian Connection Protocol.

This specification describes a reference HTTP API.

Implementations may use different transport technologies provided they preserve the semantic behavior defined by HCP.

---

# 2. Purpose

The Node API exists to expose the core capabilities of an HCP Node through a consistent interface.

Every compliant implementation should support operations for:

- Creating Humanitarian Records.
- Querying Humanitarian Records.
- Synchronizing observations.
- Monitoring node availability.

The API is intentionally minimal.

More advanced capabilities may be introduced by future specifications.

---

# 3. Design Principles

Every HCP Node API should be:

## Stateless

Every request is independent.

Servers should not require conversational state between requests.

---

## Canonical

Every exchanged Humanitarian Record must follow the Canonical JSON Specification defined in HCP-0010.

---

## Language Independent

Clients may be implemented in any programming language.

The API behavior remains identical.

---

## Extensible

Future endpoints may be added without breaking existing implementations.

---

# 4. Core Endpoints

A reference implementation should expose the following operations.

| Method | Endpoint | Purpose |
|----------|----------------|--------------------------------|
| POST | /records | Create Humanitarian Record |
| POST | /queries | Search Humanitarian Records |
| POST | /sync | Synchronize observations |
| GET | /health | Node health status |

---

# 5. Create Record

Creates a new Humanitarian Record.

Request

```http
POST /records
```

Body

```json
{
  "subject": "person",
  "event_type": "missing",
  "reported_name": "Juan Pérez",
  "estimated_age": 42,
  "recognition_features": "Blue jacket, black backpack",
  "reported_location": "Caracas",
  "reported_by": "family"
}
```

Successful Response

```http
201 Created
```

```json
{
  "record_id": "2d36d31d-c987-4c35-b0a8-74cb8eb9b62e",
  "status": "created",
  "created_at": "2026-07-07T16:30:00Z"
}
```

---

# 6. Query Records

Searches for Humanitarian Records that may describe the same humanitarian event.

Request

```http
POST /queries
```

Body

```json
{
  "subject": "person",
  "event_type": "missing",
  "reported_name": "Juan Pérez",
  "estimated_age": 42,
  "recognition_features": "Blue jacket",
  "reported_location": "Caracas"
}
```

Successful Response

```http
200 OK
```

```json
{
  "results": [
    {
      "record_id": "d71b5f...",
      "probability": 0.93,
      "status": "hospitalized"
    },
    {
      "record_id": "ab91de...",
      "probability": 0.81,
      "status": "missing"
    }
  ]
}
```

The correlation algorithm is implementation-specific.

The API only standardizes the request and response structures.

---

# 7. Synchronization

Synchronizes Humanitarian Records between HCP Nodes.

Request

```http
POST /sync
```

Body

```json
{
  "records": [
    {
      "...": "..."
    }
  ]
}
```

Successful Response

```http
202 Accepted
```

```json
{
  "accepted": 12,
  "rejected": 0
}
```

Synchronization behavior is defined in HCP-0013.

---

# 8. Health Check

Returns basic information about the node.

Request

```http
GET /health
```

Example Response

```json
{
  "status": "ok",
  "version": "0.2"
}
```

Health checks are optional but recommended.

---

# 9. Error Responses

Errors should be returned using structured JSON.

Example

```http
400 Bad Request
```

```json
{
  "error": "invalid_query",
  "message": "reported_name must be a string"
}
```

The protocol does not require a mandatory error schema.

However, implementations should return machine-readable error information whenever possible.

---

# 10. Authentication

Authentication is implementation-specific.

Possible mechanisms include:

- API Keys
- OAuth
- Mutual TLS
- JWT
- Internal Network Authentication

The HCP protocol intentionally remains independent from authentication technology.

---

# 11. Versioning

Nodes should expose their supported protocol version.

Example

```json
{
  "hcp_version": "0.2"
}
```

This allows future protocol evolution without breaking interoperability.

---

# 12. Transport Independence

Although this specification uses HTTP examples, HCP is transport-independent.

Equivalent operations may be implemented over:

- HTTPS
- gRPC
- Message Queues
- Mesh Networks
- SMS Gateways
- Satellite Links
- Local Networks

The transport mechanism does not change the semantics of the protocol.

---

# 13. Relationship with Other Specifications

This document defines the recommended API exposed by HCP Nodes.

Related specifications include:

- HCP-0001 Humanitarian Record
- HCP-0005 Node Communication Protocol
- HCP-0010 Canonical JSON Specification
- HCP-0011 Query Model
- HCP-0012 Correlation Model
- HCP-0013 Synchronization Model

Together these specifications define how applications and nodes exchange humanitarian observations across the HCP ecosystem.
