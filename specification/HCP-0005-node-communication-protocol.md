# HCP-0005

# Node Communication Protocol

Version: 0.2 (Draft)

Status: Draft

Category: Core Specification

Project: Human Connection Network (HCN)

License: Apache-2.0

Last Updated: 2026-07-13

Depends On:

- HCP-0000 — Architecture and Overview
- HCP-0001 — Humanitarian Record
- HCP-0002 — HCP Node
- HCP-0003 — Subject Model
- HCP-0004 — Correlation Model

Replaces:
None

Replaced By:
None

---

# Abstract

This document defines how independent HCP Nodes exchange humanitarian observations while preserving semantic interoperability.

The Node Communication Protocol standardizes the meaning of exchanged information rather than the technologies used to transport it.

Compatible HCP Nodes may communicate through different infrastructures while remaining interoperable by exchanging Canonical HCP JSON representations defined by the protocol.

Communication enables Humanitarian Records to be created, queried, synchronized and correlated across independent implementations without requiring shared databases or centralized identity systems.

---

# 1. Introduction

Humanitarian organizations often operate using independent software systems.

Hospitals, emergency responders, humanitarian organizations, governments and community initiatives frequently collect compatible humanitarian observations without sharing the same infrastructure.

The Node Communication Protocol enables those independent implementations to exchange humanitarian observations using the common semantic model defined by HCP.

Communication occurs between HCP Nodes.

Each Node remains fully responsible for its own infrastructure, operational policies and internal implementation.

The protocol standardizes communication semantics.

It does not standardize software architecture, databases or communication technologies.

Communication standardizes meaning, not infrastructure.

---

# 2. Purpose

The purpose of the Node Communication Protocol is to enable humanitarian interoperability between independent HCP Nodes.

The protocol allows compatible implementations to:

- create humanitarian observations;
- query humanitarian observations;
- synchronize humanitarian observations;
- exchange Canonical HCP JSON representations;
- generate explainable Correlation Candidates.

Organizations remain free to implement their own:

- programming languages;
- database technologies;
- deployment architectures;
- communication technologies;
- operational procedures.

Only the exchanged humanitarian meaning is standardized.

---

# 3. Communication Principles

Every HCP Node communication should preserve the following principles.

## Semantic Interoperability

Every exchanged Humanitarian Record should preserve the semantic definitions established by HCP.

---

## Stateless Communication

Each request should be processed independently.

Nodes should not depend on previous communication history to interpret a request.

Stateless communication improves interoperability across heterogeneous implementations.

---

## Organizational Autonomy

Every HCP Node remains independently operated.

Organizations retain complete control over:

- stored observations;
- synchronization policies;
- operational procedures;
- correlation implementation;
- security mechanisms.

The protocol never requires centralized operational control.

---

## Infrastructure Independence

The Node Communication Protocol does not prescribe:

- transport technologies;
- databases;
- programming languages;
- deployment models;
- network topologies.

Independent implementations remain interoperable through the common semantic model defined by HCP.

---

## Offline-first

Humanitarian observations may be exchanged immediately or synchronized later depending on network availability.

This allows HCP implementations to operate under intermittent, delayed or disrupted connectivity.

---

## Extensible

Future protocol versions may introduce additional communication operations while preserving backward compatibility whenever reasonably possible.

---

# 4. Core Communication Operations

Every compatible HCP implementation should support the following conceptual communication operations.

## Create Observation

Registers a new humanitarian observation.

Input:

```text
Canonical Humanitarian Record
```

Output:

```text
Record Identifier

Creation Status

Timestamp
```

---

## Query Observations

Requests Humanitarian Records that may describe the same observed Subject.

Input:

```text
Query Model
```

Output:

```text
Explainable Correlation Candidates
```
---

## Synchronize Observations

Exchanges Humanitarian Records between compatible HCP Nodes.

Synchronization allows independent observations to propagate across autonomous implementations while preserving observation independence.

Synchronization behavior is further defined in **HCP-0013 — Synchronization Model**.

---

## Health Check

An HCP Node may expose a lightweight operation indicating that it is available to receive communication.

Health Check is optional but recommended.

It is intended for operational monitoring rather than humanitarian interoperability.

---

# 5. Communication Flow

The following conceptual flow illustrates a typical interaction between independent HCP implementations.

```text
User

        │

        ▼

HCP Client

        │

        ▼

HCP Node A

(Create Observation)

        │

        ▼

Canonical Humanitarian Record

        │

        ▼

HCP Node B

(Query / Synchronize)

        │

        ▼

Local Correlation

        │

        ▼

Explainable Correlation Candidates

        │

        ▼

HCP Client

        │

        ▼

User
```

Throughout this process:

- Humanitarian Records are exchanged.
- Correlation Candidates are generated locally.
- Identity verification remains a human responsibility.

---

# 6. Data Exchange

Every exchanged Humanitarian Record shall use the **Canonical HCP JSON Representation** defined in **HCP-0010**.

Implementations may internally use:

- relational databases;
- document databases;
- object models;
- file systems;
- distributed storage;
- future storage technologies.

Those implementation details remain outside the scope of HCP.

Only the exchanged semantic representation is standardized.

This separation preserves interoperability while allowing unlimited implementation flexibility.

---

# 7. Communication Categories

Typical communication between HCP Nodes includes:

- Create Observation
- Query Observations
- Synchronize Observations
- Status Information
- Health Check

Future specifications may define additional communication categories without affecting existing interoperable implementations.

The protocol is intentionally extensible.

---

# 8. Responses

Every communication response should provide sufficient semantic information for the requesting implementation to understand the result.

Typical successful responses include:

```text
200 OK
```

Operation completed successfully.

---

```text
201 Created
```

A new Humanitarian Record was successfully created.

---

```text
202 Accepted
```

The request was accepted for asynchronous processing.

Typical unsuccessful responses include:

```text
400 Bad Request
```

Invalid protocol request.

---

```text
404 Not Found
```

Requested resource or observation not found.

---

```text
500 Internal Server Error
```

Unexpected implementation error.

Transport-specific status codes depend on the communication technology being used.

The protocol standardizes semantic behavior rather than transport-specific details.
---

# 9. Error Handling

Whenever possible, HCP Nodes should return structured error information that allows compatible implementations to understand and recover from communication failures.

Error responses should describe protocol-level problems rather than implementation-specific details.

Typical protocol errors include:

- invalid Humanitarian Record
- invalid Query Model
- unsupported protocol version
- malformed Canonical HCP JSON
- unsupported communication operation

Example:

```json
{
  "error": "invalid_query",
  "message": "reported_name must be a string"
}
```

The protocol does not prescribe a mandatory error format.

However, implementations are encouraged to provide consistent, machine-readable error information whenever practical.

---

# 10. Security

The Node Communication Protocol should use secure transport mechanisms whenever available.

Authentication, authorization, encryption and network security remain implementation-specific responsibilities.

Different HCP implementations may adopt different security models while remaining fully interoperable.

The protocol standardizes communication semantics.

It does not standardize transport security.

Additional security requirements are defined in:

- **HCP-0020 — Security Model**

---

# 11. Interoperability

An HCP Node is considered interoperable when it correctly implements the semantic communication model defined by HCP.

A compatible implementation should be capable of:

- creating Humanitarian Records from humanitarian observations;
- exchanging Canonical HCP JSON representations;
- executing protocol-compatible queries;
- returning Explainable Correlation Candidates;
- synchronizing Humanitarian Records;
- interpreting compatible protocol versions.

Interoperability is achieved through shared semantic definitions.

It is not achieved through shared software, common databases or identical implementations.

Independent HCP Nodes remain interoperable because they exchange humanitarian meaning rather than implementation details.

---

# 12. Relationship with Other Specifications

This document defines the conceptual communication model between HCP Nodes.

Additional specifications define complementary aspects of node communication.

- **HCP-0001** defines the Humanitarian Record.
- **HCP-0002** defines the HCP Node.
- **HCP-0004** defines the Correlation Model.
- **HCP-0009** defines the Node API.
- **HCP-0010** defines the Canonical HCP JSON Representation.
- **HCP-0011** defines the Query Model.
- **HCP-0013** defines the Synchronization Model.
- **HCP-0015** defines the Result Presentation Model.

Together, these specifications define how independent HCP Nodes exchange humanitarian observations while preserving semantic interoperability, organizational autonomy and implementation independence.

---

# 13. Summary

The Node Communication Protocol defines how independent HCP Nodes exchange humanitarian observations using a common semantic model.

The protocol standardizes communication semantics rather than communication technologies.

Humanitarian Records are exchanged.

Correlation Candidates are generated locally.

Identity verification remains a human responsibility.

By separating protocol semantics from transport technologies and software implementation, HCP enables hospitals, humanitarian organizations, governments, emergency responders and independent initiatives to interoperate without requiring shared infrastructure or centralized identity systems.

The Node Communication Protocol transforms independent humanitarian implementations into an interoperable humanitarian network through a shared language rather than a shared platform.
