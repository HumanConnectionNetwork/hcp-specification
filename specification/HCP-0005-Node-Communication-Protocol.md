# HCP-0005
# Node Communication Protocol

Version: 0.2 (Draft)

Status: Draft

Category: Core Specification

Authors: Human Connection Network Foundation

License: Apache-2.0

Last Updated: 2026-07-07

Depends On:

- HCP-0000 Architecture and Overview
- HCP-0001 Humanitarian Record
- HCP-0002 HCP Node

---

# 1. Introduction

This document defines how HCP Nodes communicate with one another.

The Humanitarian Connection Protocol (HCP) is designed to enable independent systems to exchange humanitarian observations using a common language.

Communication between nodes is based on standardized requests and responses rather than shared databases.

Nodes remain autonomous while interoperating through the HCP specification.

---

# 2. Purpose

The purpose of the Node Communication Protocol is to guarantee interoperability between HCP Nodes.

Regardless of the programming language, operating system, database or infrastructure used, every compliant node must be capable of:

- Creating Humanitarian Records.
- Querying Humanitarian Records.
- Receiving Correlation Candidates.
- Synchronizing humanitarian observations.
- Exchanging structured responses.

The protocol intentionally avoids defining implementation details such as databases or application frameworks.

---

# 3. Communication Principles

Every HCP Node communication follows these principles.

## Standardized

Nodes exchange information using the canonical structures defined by HCP.

---

## Stateless

Each request is independent.

Nodes should not require previous communication history to process a request.

---

## Decentralized

Nodes communicate directly without requiring a central authority.

Each node remains responsible for its own data and decisions.

---

## Offline-Friendly

Communication mechanisms should support environments with intermittent connectivity.

Synchronization may occur immediately or later.

---

## Extensible

Future protocol versions may introduce additional operations while maintaining backward compatibility.

---

# 4. Core Operations

Every HCP implementation should support four fundamental operations.

## Create Record

Creates a new Humanitarian Record.

Input:

```
Humanitarian Record
```

Output:

```
Record Identifier
Creation Status
Timestamp
```

---

## Query Records

Searches for Humanitarian Records that may describe the same humanitarian event.

Input:

```
Query
```

Output:

```
Correlation Candidates
```

---

## Synchronize Records

Exchanges Humanitarian Records between HCP Nodes.

Synchronization allows distributed humanitarian observations to propagate across independent implementations.

Synchronization details are defined in HCP-0013.

---

## Health Check

Nodes may expose a simple endpoint indicating that they are available to receive requests.

This operation is optional but recommended.

---

# 5. Communication Flow

A typical interaction between two HCP Nodes follows this sequence.

```
Node A

↓

Create Record

↓

Node B stores the observation

↓

Node C submits a Query

↓

Node B evaluates correlation

↓

Node B returns Correlation Candidates
```

Nodes do not exchange identities.

They exchange humanitarian observations.

---

# 6. Data Exchange

Every exchanged payload must follow the canonical JSON representation defined by HCP-0010.

Implementations may internally use different databases or object models.

Only the exchanged representation is standardized.

---

# 7. Request Types

Typical request categories include:

- Create Record
- Query
- Synchronization
- Status
- Health Check

Future specifications may introduce additional operations.

---

# 8. Responses

Every response should contain enough information for the requesting node to understand the result.

Typical responses include:

Success

```
200 OK
```

Created

```
201 Created
```

Accepted

```
202 Accepted
```

Bad Request

```
400 Bad Request
```

Not Found

```
404 Not Found
```

Internal Error

```
500 Internal Server Error
```

Transport-specific status codes depend on the implementation.

---

# 9. Error Handling

Nodes should return structured error information whenever possible.

Errors should be descriptive enough to allow implementations to recover automatically.

Example:

```json
{
  "error": "invalid_query",
  "message": "reported_name must be a string"
}
```

The protocol does not prescribe a mandatory error format but encourages consistency across implementations.

---

# 10. Security

Communication between nodes should use secure transport mechanisms whenever available.

Authentication, authorization and encryption are implementation-specific and are further described in HCP-0020.

The protocol itself remains transport-independent.

---

# 11. Interoperability

An HCP Node is considered interoperable when it can:

- Create Humanitarian Records.
- Receive Humanitarian Records.
- Execute Queries.
- Return Correlation Candidates.
- Synchronize observations.
- Interpret canonical HCP JSON structures.

Interoperability is achieved through adherence to the specification rather than through a common software implementation.

---

# 12. Relationship with Other Specifications

This document defines how HCP Nodes communicate.

Complementary specifications include:

- HCP-0001 Humanitarian Record
- HCP-0010 Canonical JSON Specification
- HCP-0011 Query Model
- HCP-0012 Correlation Model
- HCP-0013 Synchronization Model
- HCP-0015 Result Presentation Model

Together these specifications define the complete communication lifecycle between HCP Nodes.
