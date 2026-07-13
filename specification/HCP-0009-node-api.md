# HCP-0009

# Node API

Version: 0.3 (Draft)

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
- HCP-0010 — Canonical JSON Specification
- HCP-0011 — Query Model

Replaces:
None

Replaced By:
None

---

# Abstract

This document defines the reference HTTP API exposed by an HCP Node.

The Node API provides a standardized HTTP interface through which applications, bots, mobile clients, hospital systems and other HCP Nodes interact with implementations of the Humanitarian Connection Protocol.

This specification defines a recommended HTTP binding.

It is not the protocol itself.

Compatible implementations may expose equivalent interfaces using different communication technologies while preserving the semantic behavior defined by HCP.

The API exists to make HCP semantics accessible through HTTP without constraining implementation architecture.

---

# 1. Introduction

The Humanitarian Connection Protocol defines semantic interoperability between independent humanitarian systems.

The Node Communication Protocol defines how HCP Nodes conceptually exchange humanitarian observations.

This document defines a reference HTTP API implementing that communication model.

The API provides a practical interface allowing HCP Clients and HCP Nodes to:

- create humanitarian observations;
- search compatible observations;
- synchronize Humanitarian Records;
- monitor node availability.

Although HTTP is used throughout this specification, HCP remains transport-independent.

Equivalent APIs may be implemented using different communication technologies while preserving identical semantic behavior.

---

# 2. Purpose

The purpose of the Node API is to expose the semantic capabilities of an HCP Node through a consistent HTTP interface.

The API enables compatible implementations to:

- create humanitarian observations;
- search compatible observations;
- synchronize Humanitarian Records;
- retrieve node status information.

The API intentionally remains minimal.

Advanced capabilities may be introduced by future specifications without affecting interoperability.

The protocol standardizes humanitarian semantics.

The API exposes those semantics through HTTP.

---

# 3. Design Principles

Every HCP Node API should preserve the following principles.

## Semantic

The API exposes HCP semantic concepts.

It does not expose implementation details.

---

## Stateless

Every request should be processed independently.

Servers should not depend on conversational state between requests.

Stateless communication improves interoperability between heterogeneous implementations.

---

## Canonical

Every exchanged Humanitarian Record shall follow the Canonical HCP JSON Representation defined by **HCP-0010**.

---

## Language Independent

Clients may be implemented using any programming language.

The API behavior remains semantically identical.

---

## Extensible

Future API operations may be introduced without breaking existing compatible implementations.

---

# 4. Reference Endpoints

A reference HTTP implementation should expose the following operations.

| Method | Endpoint | Purpose |
|---------|----------------|---------------------------------------------|
| POST | `/observations` | Create a humanitarian observation |
| POST | `/search` | Search compatible observations |
| POST | `/sync` | Synchronize Humanitarian Records |
| GET | `/health` | Retrieve node health information |

These endpoints represent the recommended HTTP binding for HCP.

Equivalent operations may be implemented using different transport technologies while preserving the same semantic behavior.
---

# 5. Create Observation

Creates a new humanitarian observation.

The submitted Observation shall be transformed by the HCP Node into a Humanitarian Record represented using the Canonical HCP JSON Specification.

Request

```http
POST /observations
```

Request Body

The request body shall follow the Canonical HCP JSON Representation defined in **HCP-0010**.

Illustrative example:

```json
{
  "subject": "human",
  "event_type": "missing_report",
  "status": "missing",
  "reported_label": "Juan Pérez",
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
  "created_at": "2026-07-13T16:30:00Z"
}
```

The HTTP API creates an Observation.

The HCP Node creates the corresponding Humanitarian Record.

---

# 6. Search Observations

Searches for compatible humanitarian observations.

The HCP Node evaluates available Humanitarian Records using its locally implemented Correlation Model.

Request

```http
POST /search
```

Request Body

The request body shall follow the Query Model defined in **HCP-0011**.

Illustrative example:

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

Successful Response

```http
200 OK
```

```json
{
  "results": [
    {
      "record_id": "d71b5f...",
      "score": 0.93,
      "event_type": "hospital_admission",
      "status": "stable",
      "explanation": [
        "Reported labels are compatible",
        "Estimated ages are compatible",
        "Recognition Features are compatible",
        "Locations are geographically compatible"
      ]
    },
    {
      "record_id": "ab91de...",
      "score": 0.81,
      "event_type": "missing_report",
      "status": "missing",
      "explanation": [
        "Recognition Features are compatible",
        "Reported locations are compatible"
      ]
    }
  ]
}
```

The correlation algorithm remains implementation-specific.

The API standardizes only the request and response semantics.

---

# 7. Synchronization

Synchronizes Humanitarian Records between compatible HCP Nodes.

Request

```http
POST /sync
```

Request Body

```json
{
  "records": [
    {
      "...": "Canonical HCP JSON..."
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

Synchronization behavior is defined in **HCP-0013 — Synchronization Model**.

The API defines only the HTTP binding.

---

# 8. Health Check

Returns operational information about the HCP Node.

Request

```http
GET /health
```

Example Response

```json
{
  "status": "ok",
  "hcp_version": "0.3",
  "node_version": "1.2.0"
}
```

Health Check is intended for operational monitoring.

It is not part of humanitarian interoperability.

---

# 9. Error Responses

Whenever possible, HCP Nodes should return structured, machine-readable error information.

Example

```http
400 Bad Request
```

```json
{
  "error": "invalid_query",
  "message": "reported_label must be a string"
}
```

Error responses should describe protocol-level problems.

They should avoid exposing implementation-specific details whenever reasonably possible.

The protocol does not prescribe a mandatory error schema.

However, consistent machine-readable responses are strongly encouraged.
---

# 10. Authentication

Authentication and authorization remain outside the scope of the Humanitarian Connection Protocol.

Different HCP implementations may adopt authentication mechanisms appropriate to their operational environment.

Examples include:

- API Keys
- OAuth 2.0
- Mutual TLS
- JWT
- Internal Network Authentication
- Future authentication technologies

Authentication mechanisms do not affect protocol interoperability.

The protocol standardizes humanitarian semantics.

Implementations define authentication.

---

# 11. Versioning

Every HCP Node should expose the versions it supports.

Example:

```json
{
  "hcp_version": "0.3",
  "node_version": "1.2.0"
}
```

Where:

- **hcp_version** identifies the supported Humanitarian Connection Protocol version.
- **node_version** identifies the software implementation version.

Separating protocol version from implementation version improves interoperability and simplifies protocol evolution.

---

# 12. Transport Independence

This specification defines a reference HTTP binding.

The Humanitarian Connection Protocol itself remains transport-independent.

Equivalent semantic behavior may be implemented using technologies such as:

- HTTPS
- HTTP/2
- gRPC
- Message Queues
- MQTT
- Mesh Networks
- SMS Gateways
- Satellite Communication
- Local Networks
- Future communication technologies

Changing the transport mechanism never changes the semantic meaning of the exchanged humanitarian information.

The protocol standardizes humanitarian semantics.

Transport technologies deliver those semantics.

---

# 13. Relationship with Other Specifications

This document defines the recommended HTTP interface exposed by HCP Nodes.

Complementary specifications define the remaining layers of the protocol.

- **HCP-0001** defines the Humanitarian Record.
- **HCP-0002** defines the HCP Node.
- **HCP-0005** defines the Node Communication Protocol.
- **HCP-0010** defines the Canonical HCP JSON Representation.
- **HCP-0011** defines the Query Model.
- **HCP-0012** defines the Correlation Model.
- **HCP-0013** defines the Synchronization Model.

Together, these specifications define how independent HCP implementations expose, exchange and synchronize humanitarian observations while preserving semantic interoperability.

---

# 14. Summary

The Node API defines the recommended HTTP interface for exposing the capabilities of an HCP Node.

It is a reference HTTP binding.

It is not the Humanitarian Connection Protocol itself.

The protocol defines humanitarian semantics.

The Node Communication Protocol defines conceptual communication.

The Node API exposes that communication through HTTP.

Reference implementations transform humanitarian observations into Humanitarian Records.

Clients submit observations.

Nodes generate Humanitarian Records.

Nodes correlate observations.

Nodes synchronize Humanitarian Records.

People interpret results.

People verify reality.

By separating protocol semantics, communication behavior, transport technologies and software implementation, HCP enables independent organizations to build interoperable humanitarian systems without requiring shared software, centralized databases or global identity systems.

The Node API demonstrates one of the fundamental architectural principles of HCP:

**The protocol standardizes semantics.**

**The communication model standardizes interaction.**

**The API standardizes HTTP exposure.**

**Implementations remain free.**
