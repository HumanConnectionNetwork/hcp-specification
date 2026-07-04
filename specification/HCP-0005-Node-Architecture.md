# HCP-0005

# Humanitarian Connection Protocol
## Node Architecture

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

---

# 1. Abstract

An HCP Node is the software service responsible for implementing the Humanitarian Connection Protocol.

It provides the core functionality required to create, store, query, correlate, validate and exchange Humanitarian Records.

An HCP Node is not a user interface.

It is not a Telegram Bot, a mobile application or a website.

Those systems are HCP Clients.

The Node is the protocol implementation.

---

# 2. Purpose

The purpose of an HCP Node is to implement the protocol independently of any specific application.

Every interaction with HCP is performed through a Node.

Applications communicate with Nodes.

Nodes communicate with other Nodes.

---

# 3. Fundamental Principle

A Client provides access to HCP.

A Node implements HCP.

Clients never communicate directly with other Clients.

Nodes exchange Humanitarian Records with other Nodes according to the HCP specification.

---

# 4. Node Responsibilities

Every HCP Node performs five fundamental responsibilities.

## 4.1 Create

Receive humanitarian observations from Clients.

Validate the received information.

Create a valid Humanitarian Record.

Store the record locally.

---

## 4.2 Query

Search Humanitarian Records stored in the local repository.

Return matching observations.

Support correlation requests.

---

## 4.3 Correlate

Analyze Humanitarian Records.

Generate Person Candidates.

Reconstruct Humanitarian Timelines.

Determine the Last Known Status.

Correlation is always performed locally.

Person Candidates are never synchronized with other Nodes.

---

## 4.4 Synchronize

Exchange Humanitarian Records with other HCP Nodes.

Synchronization only exchanges Humanitarian Records.

Nodes never synchronize:

- Person Candidates
- Humanitarian Timelines
- Correlation scores
- Search results

Each Node performs its own correlation independently.

---

## 4.5 Validate

Verify that incoming Humanitarian Records comply with the HCP specification.

Reject malformed or incompatible records.

Validation guarantees interoperability.

---

# 5. Node Components

A compliant HCP Node is conceptually composed of several internal components.

## Record Engine

Responsible for creating and validating Humanitarian Records.

---

## Repository

Stores Humanitarian Records locally.

The repository belongs exclusively to the Node operator.

HCP does not prescribe any database technology.

---

## Query Engine

Searches Humanitarian Records.

Supports structured queries.

Provides data for correlation.

---

## Correlation Engine

Analyzes Humanitarian Records.

Generates Person Candidates.

Builds Humanitarian Timelines.

Determines Last Known Status.

This engine is local to every Node.

---

## Synchronization Engine

Communicates with other HCP Nodes.

Exchanges Humanitarian Records.

Maintains protocol interoperability.

---

## Validation Engine

Verifies protocol compliance.

Checks schema compatibility.

Ensures incoming data satisfies HCP requirements.

---

# 6. Local Repository

Every Node maintains its own repository.

HCP does not define:

- database engine;
- storage model;
- cloud provider;
- indexing strategy.

Implementations remain free to choose any technology.

---

# 7. Clients

Clients are applications that interact with an HCP Node.

Examples include:

- Telegram Bots
- WhatsApp Bots
- Mobile applications
- Web applications
- Hospital systems
- Government systems
- NGO platforms
- SDKs
- Command-line tools

Clients do not implement HCP.

They consume HCP through a Node.

---

# 8. Node Independence

Each Node operates independently.

Nodes may differ in:

- hardware;
- operating system;
- programming language;
- database engine;
- search algorithms;
- correlation algorithms;
- deployment model.

As long as they comply with HCP, interoperability is preserved.

---

# 9. Node Communication

Nodes communicate exclusively through standardized protocol messages.

Nodes never exchange:

- user interfaces;
- databases;
- application logic;
- Person Candidates.

Only Humanitarian Records and protocol-defined messages are exchanged.

---

# 10. Internal Intelligence

HCP intentionally separates protocol interoperability from implementation intelligence.

Every Node may implement:

- optimized search;
- probabilistic correlation;
- artificial intelligence;
- machine learning;
- custom ranking algorithms.

These capabilities improve local performance without affecting protocol compatibility.

---

# 11. Scalability

Nodes may operate:

- on personal computers;
- on cloud infrastructure;
- on government infrastructure;
- on hospital servers;
- on humanitarian organization networks;
- on edge devices.

The protocol imposes no deployment restrictions.

---

# 12. Security

Each Node is responsible for protecting:

- its infrastructure;
- its repository;
- its communications;
- its operational environment.

Future HCP specifications define transport security and authentication.

---

# 13. Compliance

A compliant HCP Node shall:

- create valid Humanitarian Records;
- store records locally;
- support standardized queries;
- perform local correlation;
- synchronize Humanitarian Records with other Nodes;
- validate incoming records;
- preserve protocol interoperability.

---

# 14. Reference Architecture

A typical HCP implementation follows this conceptual architecture:

```text
                Clients
                   │
     ┌─────────────┼─────────────┐
     │             │             │
 Telegram Bot   Mobile App   Hospital System
     │             │             │
     └─────────────┼─────────────┘
                   │
             HCP NODE
                   │
     ┌─────────────┼─────────────┐
     │             │             │
 Record      Correlation     Validation
 Engine        Engine          Engine
     │             │             │
     └─────────────┼─────────────┘
                   │
            Local Repository
                   │
          Synchronization Engine
                   │
             Other HCP Nodes
```

---

# 15. Summary

An HCP Node is the software service that implements the Humanitarian Connection Protocol.

It is responsible for creating, storing, querying, correlating, validating and synchronizing Humanitarian Records.

Clients provide access to the protocol.

Nodes implement the protocol.

This separation allows applications to evolve independently while preserving interoperability between all HCP implementations.
