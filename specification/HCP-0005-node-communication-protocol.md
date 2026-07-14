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
- HCP-0013 — Synchronization Model

Replaces:
None

Replaced By:
None

---

# Abstract

This document defines the semantic communication model between independent HCP Nodes.

The Node Communication Protocol specifies how autonomous implementations exchange Humanitarian Records while preserving semantic interoperability.

The protocol standardizes humanitarian meaning.

It does not standardize transport technologies, software architectures or communication infrastructures.

Communication enables independent Nodes to exchange humanitarian evidence while preserving organizational autonomy, implementation independence and local interpretation.

---

# 1. Introduction

Humanitarian organizations frequently operate using independent software systems.

Hospitals, emergency responders, humanitarian organizations, governments, community initiatives and digital platforms often collect compatible humanitarian observations without sharing the same infrastructure.

The Node Communication Protocol enables those independent implementations to exchange Humanitarian Records using the common semantic language defined by HCP.

Communication occurs between HCP Nodes.

Each Node remains fully responsible for its own:

- infrastructure;
- operational policies;
- synchronization strategy;
- internal implementation;
- correlation methods.

The protocol standardizes communication semantics.

It does not prescribe software architectures, databases, transport technologies or deployment models.

Communication standardizes humanitarian meaning.

It does not standardize implementation.

---

# 2. Purpose

The purpose of the Node Communication Protocol is to enable semantic interoperability between autonomous HCP Nodes.

Rather than requiring organizations to replace their existing software or adopt centralized platforms, HCP enables independent implementations to communicate through a shared humanitarian language.

The protocol allows Nodes to:

- create Humanitarian Records;
- query Humanitarian Records;
- synchronize Humanitarian Records;
- exchange Canonical HCP JSON representations.

Interpretation always remains local.

Evidence is exchanged.

Humanitarian understanding is never synchronized.

Organizations remain free to define their own:

- programming languages;
- databases;
- communication technologies;
- deployment architectures;
- operational procedures.

Only humanitarian meaning is standardized.

---

# 3. Communication Philosophy

The Node Communication Protocol follows one fundamental architectural principle.

Nodes exchange humanitarian evidence.

They do not exchange humanitarian interpretation.

Consequently:

- Humanitarian Records are exchanged.
- Humanitarian Cases are never exchanged.
- Correlation Candidates are never exchanged.
- Correlation remains local.
- Presentation remains local.
- Human verification remains outside the protocol.

This separation preserves semantic interoperability while allowing independent implementations to continuously improve their internal processing without affecting communication with other Nodes.

---

# 4. Communication Principles

Every Node communication should preserve the following principles.

## Semantic Interoperability

Every exchanged Humanitarian Record should preserve the humanitarian meaning defined by HCP.

---

## Stateless Communication

Each communication should be interpreted independently.

Nodes should not require previous communication history to understand exchanged Humanitarian Records.

---

## Organizational Autonomy

Every HCP Node remains independently operated.

Organizations retain complete control over:

- stored Humanitarian Records;
- synchronization policies;
- correlation strategies;
- security mechanisms;
- operational procedures.

The protocol never requires centralized operational control.

---

## Implementation Independence

The Node Communication Protocol does not prescribe:

- transport technologies;
- databases;
- programming languages;
- deployment models;
- communication infrastructures.

Independent implementations remain interoperable because they exchange the same humanitarian meaning.

---

## Synchronization Independence

Communication does not imply synchronization.

Synchronization does not imply federation.

Federation does not imply permanent communication.

Each Node independently decides when and how Humanitarian Records are exchanged.
---
# 5. Communication Operations

The Node Communication Protocol defines the conceptual communication operations performed between autonomous HCP Nodes.

These operations describe humanitarian meaning rather than specific APIs, transport mechanisms or implementation technologies.

The protocol currently defines four fundamental communication operations.

---

## Create Humanitarian Record

A Node may receive a new Humanitarian Record created from a Humanitarian Observation.

The receiving Node validates the Canonical HCP JSON representation according to the protocol specification.

Successful creation does not imply synchronization with other Nodes.

---

## Query Humanitarian Records

A Node may receive a query describing humanitarian evidence.

The Node evaluates its locally available Humanitarian Records.

Query processing always remains local.

Only Humanitarian Records are evaluated.

Correlation and presentation occur afterwards according to local implementation rules.

---

## Synchronize Humanitarian Records

Independent Nodes may exchange Humanitarian Records through synchronization.

Synchronization distributes humanitarian observations.

It never distributes:

- Humanitarian Cases;
- Correlation Candidates;
- local interpretation.

Synchronization behavior is fully defined in **HCP-0013 — Synchronization Model**.

---

## Discover Available Information

A Node may expose information allowing other Nodes to determine what humanitarian information may be available for synchronization or query.

The discovery mechanism is implementation-specific.

Discovery does not imply:

- federation;
- synchronization;
- trust;
- authorization.

Those concepts are defined independently by other HCP specifications.

---

# 6. Communication Flow

The conceptual communication flow defined by HCP is illustrated below.

```text
Humanitarian Observation

        │

        ▼

Humanitarian Record

        │

        ▼

Node Communication

        │

        ▼

Synchronization

        │

        ▼

Query

        │

        ▼

Local Correlation

        │

        ▼

Humanitarian Case

        │

        ▼

Presentation

        │

        ▼

Human Verification
```

Each stage has a distinct responsibility.

Communication exchanges humanitarian evidence.

Interpretation always remains local.

---

# 7. Data Exchange

Every exchanged Humanitarian Record shall use the Canonical HCP JSON representation defined in **HCP-0010**.

Implementations remain free to use any internal representation including:

- relational databases;
- document databases;
- object models;
- distributed storage;
- file systems;
- future storage technologies.

Internal implementation details remain outside the scope of HCP.

Only the exchanged humanitarian meaning is standardized.

This separation enables unlimited implementation flexibility while preserving interoperability.

---

# 8. Interoperability

Two HCP Nodes are interoperable when they exchange Humanitarian Records while preserving the semantic definitions established by the protocol.

Interoperability does not require:

- identical software;
- identical databases;
- identical infrastructures;
- identical APIs;
- identical correlation algorithms.

Instead, interoperability depends upon shared semantic understanding.

Different implementations may internally process humanitarian information differently while exchanging semantically compatible Humanitarian Records.

Shared meaning replaces shared infrastructure.

---

# 9. Relationship with Other Specifications

This document defines the semantic communication model between HCP Nodes.

Additional specifications define complementary aspects of humanitarian interoperability.

```text
HCP-0001
Humanitarian Record
        │
        ▼
HCP-0005
Node Communication
        │
        ├───────────────┐
        ▼               ▼
HCP-0009          HCP-0013
Node API      Synchronization
        │               │
        └───────┬───────┘
                ▼
          HCP-0011
        Query Model
                │
                ▼
          HCP-0012
       Correlation Model
                │
                ▼
          HCP-0015
     Result Presentation
```

Each specification has a distinct responsibility.

- **HCP-0005** defines what communication means.
- **HCP-0009** defines one possible API for that communication.
- **HCP-0010** defines the Canonical JSON representation.
- **HCP-0011** defines humanitarian queries.
- **HCP-0012** defines local correlation.
- **HCP-0013** defines synchronization.
- **HCP-0015** defines local presentation.

Together, these specifications define how autonomous HCP Nodes exchange humanitarian evidence while preserving semantic interoperability and implementation independence.

---

# 10. Summary

The Node Communication Protocol defines the semantic communication model between autonomous HCP Nodes.

Nodes exchange Humanitarian Records.

Nodes never exchange Humanitarian Cases.

Nodes never exchange Correlation Candidates.

Communication distributes humanitarian evidence.

Interpretation remains local.

Human verification determines reality.

By separating communication semantics from transport technologies, software architectures and infrastructure, HCP enables independent humanitarian organizations to collaborate using a common semantic language without requiring centralized databases, shared software platforms or common implementation technologies.

Nodes exchange humanitarian evidence.

Implementations create humanitarian understanding.

People determine reality.
