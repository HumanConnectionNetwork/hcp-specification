# HCP-0009

# Humanitarian Connection Protocol
## Node Communication Protocol

Version: 0.1 (Draft)

Status: Draft

Category: Core Specification

Project: Human Connection Network (HCN)

License: Apache-2.0

Last Updated: 2026-07-04

Depends On:

- HCP-0000 — Architecture and Overview
- HCP-0001 — Fundamental Principles
- HCP-0002 — Humanitarian Record
- HCP-0003 — Subject Model
- HCP-0004 — Person Correlation Model
- HCP-0005 — Node Architecture
- HCP-0006 — Observation Model
- HCP-0007 — Status Model
- HCP-0008 — Record Schema

---

# 1. Abstract

The Node Communication Protocol defines how HCP Nodes exchange information.

Communication occurs exclusively between HCP Nodes.

Clients never communicate directly with other Nodes.

The protocol defines the semantic messages exchanged between Nodes while remaining independent of any transport technology.

---

# 2. Purpose

The purpose of this specification is to establish a common communication model that allows independent HCP Nodes to interoperate regardless of programming language, infrastructure or transport mechanism.

---

# 3. Communication Principles

Node communication follows these principles:

- Decentralized
- Stateless whenever possible
- Transport independent
- Extensible
- Interoperable
- Secure by design
- Backward compatible

---

# 4. Node Roles

During communication, every Node may act as:

Requester

A Node initiating a protocol message.

Responder

A Node processing and responding to a protocol message.

A Node may perform both roles simultaneously.

---

# 5. Communication Model

Node communication consists of structured protocol messages.

Conceptually:

```text
Node A

↓

Protocol Message

↓

Node B

↓

Protocol Response

↓

Node A
```

The protocol defines messages.

It does not define how messages are transported.

---

# 6. Message Types

The HCP Core defines the following communication categories.

### Query

Request humanitarian information.

---

### Record Exchange

Transfer Humanitarian Records.

---

### Synchronization

Exchange changes between Nodes.

---

### Capability Discovery

Determine protocol capabilities supported by another Node.

---

### Validation

Verify protocol compliance.

---

### Error

Communicate protocol failures.

---

Future HCP specifications may introduce additional message categories.

---

# 7. Record Exchange

Nodes exchange only Humanitarian Records.

Nodes never exchange:

- Person Candidates
- Humanitarian Timelines
- Correlation scores
- Internal indexes
- Local databases

Each Node reconstructs humanitarian histories independently.

---

# 8. Query Messages

Query messages request humanitarian observations.

Typical queries include:

- Search by person name
- Search by UUID
- Search by location
- Search by date
- Search by observation type
- Search by validator
- Search by status

The protocol does not define ranking algorithms.

---

# 9. Synchronization Messages

Synchronization exchanges Humanitarian Records created after a given point in time.

Synchronization shall preserve:

- record immutability;
- historical integrity;
- protocol semantics.

Synchronization never overwrites existing Humanitarian Records.

---

# 10. Capability Discovery

Nodes may request capability information from other Nodes.

Examples include:

- Supported HCP version
- Supported schema versions
- Supported extensions
- Supported vocabularies

Capability Discovery improves interoperability between heterogeneous implementations.

---

# 11. Validation Messages

Nodes may validate protocol compatibility before exchanging information.

Validation may include:

- protocol version;
- schema version;
- extension compatibility.

---

# 12. Error Messages

Protocol errors shall be communicated using structured messages.

Errors should indicate:

- error category;
- error code;
- human-readable description;
- optional diagnostic information.

Future specifications define standardized error codes.

---

# 13. Transport Independence

The Node Communication Protocol is independent of transport technology.

Possible transports include:

- HTTPS
- gRPC
- Message Queues
- Offline synchronization
- Satellite communication
- Local network communication
- Future transport technologies

Transport mechanisms shall not modify protocol semantics.

---

# 14. Security

Authentication, authorization, encryption and integrity verification are defined by future HCP specifications.

The communication model remains independent from security mechanisms.

---

# 15. Extensibility

Future HCP versions may define:

- new message categories;
- additional protocol headers;
- optional capabilities;
- extension namespaces.

Existing implementations should ignore unknown optional elements whenever possible.

---

# 16. Compliance

A compliant implementation shall:

- exchange Humanitarian Records only;
- preserve record immutability;
- support protocol message semantics;
- remain transport independent;
- preserve backward compatibility.

---

# 17. Summary

The Node Communication Protocol defines how independent HCP Nodes exchange humanitarian information.

Rather than prescribing a transport technology, HCP standardizes the semantic messages exchanged between Nodes.

This separation allows HCP to remain independent of networking technologies while ensuring long-term interoperability between humanitarian systems.
