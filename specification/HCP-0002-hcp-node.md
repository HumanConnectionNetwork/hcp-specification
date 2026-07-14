# HCP-0002

# HCP Node

Version: 0.2 (Draft)

Status: Draft

Category: Core Specification

Project: Human Connection Network (HCN)

License: Apache-2.0

Last Updated: 2026-07-13

Depends On:

- HCP-0000 — Architecture and Overview
- HCP-0001 — Humanitarian Record

Replaces:
None

Replaced By:
None

---

# Abstract

This document defines the concept of an HCP Node, the fundamental implementation component of the Humanitarian Connection Protocol (HCP).

An HCP Node is an autonomous implementation of the protocol capable of producing, consuming and exchanging Humanitarian Records while preserving semantic interoperability with other compatible implementations.

Nodes implement the common language defined by HCP.

They do not define humanitarian meaning.

They do not establish humanitarian truth.

Instead, they enable independent organizations to exchange humanitarian observations while preserving organizational autonomy, technological independence and local interpretation.

This document defines the conceptual responsibilities and capabilities of an HCP Node independently of any programming language, database, software architecture or deployment model.

---

# 1. Introduction

An HCP Node is an autonomous implementation of the Humanitarian Connection Protocol.

Its purpose is to implement the HCP specification and enable Humanitarian Records to be created, exchanged, queried and processed using the common semantic model defined by the protocol.

An HCP Node is not defined by:

- a programming language;
- a database technology;
- a deployment architecture;
- a communication mechanism;
- a software framework.

Instead, an HCP Node is defined by its ability to preserve the semantic behavior specified by HCP.

Different Nodes may implement different subsets of the protocol while remaining fully interoperable.

Clients interact with HCP Nodes.

HCP Nodes interact with other HCP Nodes.

Together they create a decentralized humanitarian ecosystem based on shared meaning rather than shared infrastructure.

---

# 2. Purpose

The purpose of an HCP Node is to enable semantic interoperability between independent humanitarian implementations.

Rather than requiring organizations to replace their existing software or adopt centralized platforms, an HCP Node allows them to participate in the HCP ecosystem while preserving complete organizational autonomy.

An HCP Node enables organizations to exchange humanitarian observations using the common language defined by HCP.

Evidence can therefore be exchanged universally while interpretation remains local.

The protocol standardizes humanitarian meaning.

Each implementation remains free to choose its own technologies, operational procedures and internal architecture.

---

# 3. Node Capabilities

An HCP Node may implement one or more protocol capabilities.

Typical capabilities include:

- Humanitarian Record creation;
- Humanitarian Record consumption;
- query processing;
- synchronization;
- local correlation;
- Humanitarian Case presentation;
- explainable correlation.

The protocol does not require every Node to implement every capability.

For example:

- a hospital Node may only create and synchronize Humanitarian Records;
- a Telegram Node may create, query and present Humanitarian Cases;
- a synchronization gateway may only exchange Humanitarian Records;
- an analytics platform may perform correlation without creating new observations.

All of these implementations remain valid HCP Nodes because they preserve the semantic behavior defined by the protocol.

---

# 4. Responsibilities

Every HCP Node is responsible for correctly implementing the semantic behavior defined by the HCP specification.

Its responsibilities may include:

- creating Humanitarian Records;
- consuming Humanitarian Records;
- querying Humanitarian Records;
- synchronizing Humanitarian Records;
- correlating Humanitarian Records;
- presenting Humanitarian Cases;
- explaining correlation results.

The exact feature set depends on the implementation.

However, every compliant Node should preserve:

- semantic interoperability;
- observation integrity;
- protocol compatibility;
- implementation independence.

An HCP Node implements protocol behavior.

It does not determine permanent identity.

Human verification always remains outside the scope of the protocol.
---
# 5. Humanitarian Records

The primary responsibility of an HCP Node is to produce, consume and exchange Humanitarian Records.

Humanitarian Records are the canonical representation of Humanitarian Observations.

Each Humanitarian Record represents a single humanitarian observation concerning a living being affected by a humanitarian event.

Current HCP specifications support observations related to:

- Humans;
- Animals.

Nodes exchange Humanitarian Records.

They do not exchange identities.

They do not exchange Humanitarian Cases.

Multiple HCP Nodes may independently create Humanitarian Records describing the same humanitarian reality.

Those records remain independent observations until local correlation suggests they may contribute to the same Humanitarian Case.

Evidence is exchanged.

Interpretation remains local.

---

# 6. HCP Clients

An HCP Client is not an HCP Node.

An HCP Client provides interaction between people and an HCP Node.

Clients collect user input, present humanitarian information and facilitate user workflows.

Nodes implement the protocol.

Clients implement the user experience.

Typical HCP Clients include:

- Telegram Bots;
- WhatsApp applications;
- SMS interfaces;
- Web applications;
- Mobile applications;
- Desktop applications;
- API consumers;
- future compatible interfaces.

An HCP Client may communicate with:

- a local HCP Node;
- a remote HCP Node;
- an embedded HCP Node.

The protocol does not prescribe how Clients and Nodes are deployed.

Only their semantic interaction is standardized.

This separation allows different user interfaces to coexist while preserving a common interoperability model.

---

# 7. Communication

HCP Nodes communicate by exchanging Humanitarian Records according to the protocol specification.

The protocol defines the semantic structure of exchanged information.

It does not prescribe the transport technology.

Compatible implementations may communicate using technologies such as:

- HTTPS;
- local networks;
- mesh networks;
- satellite communication;
- store-and-forward synchronization;
- removable media;
- offline synchronization;
- future communication technologies.

Transport mechanisms may evolve independently of HCP.

Semantic interoperability remains constant.

Shared meaning replaces shared infrastructure.

---

# 8. Correlation

Correlation is a local capability of an HCP Node.

The protocol does not prescribe a specific correlation algorithm.

Instead, it defines the humanitarian evidence that implementations may evaluate when estimating relationships between Humanitarian Records.

Typical correlation evidence may include:

- Reported Label;
- estimated age;
- reported location;
- observation time;
- Event Type;
- Recognition Features;
- reporting source;
- protocol-defined metadata.

Correlation evaluates humanitarian evidence.

It does not establish identity.

It does not modify Humanitarian Records.

It produces local interpretation.

Different HCP Nodes may reach different conclusions while remaining fully interoperable because interoperability depends on shared observations rather than shared interpretation.

---

# 9. Explainability

Whenever an HCP Node produces Correlation Candidates or Humanitarian Cases, it should also provide an explanation describing the humanitarian evidence that contributed to that interpretation.

Typical explanations may include:

- Supporting Evidence;
- Conflicting Evidence;
- compatible locations;
- compatible observation times;
- compatible Recognition Features;
- compatible humanitarian status;
- event evolution.

Explainability supports human verification.

It never replaces human judgment.

Transparent reasoning enables humanitarian workers to understand why observations appear related and to evaluate local interpretations with confidence.

The complete Explainable Correlation Model is defined in **HCP-0014**.
---
# 10. Privacy and Security

An HCP Node should exchange only the humanitarian information necessary to preserve semantic interoperability.

Implementations should minimize the collection, storage and exchange of personally identifiable information whenever possible.

Whenever equivalent humanitarian value can be achieved through humanitarian observations, implementations should prefer observation-based evidence over permanent identifiers.

Security mechanisms remain implementation-specific.

Each organization may define its own:

- authentication mechanisms;
- authorization policies;
- encryption methods;
- operational security procedures.

HCP standardizes humanitarian interoperability.

It does not standardize operational security.

Additional requirements are defined in:

- **HCP-0020 — Security Model**
- **HCP-0021 — Privacy and Data Minimization**

---

# 11. Design Principles

Every HCP Node should preserve the architectural principles defined by HCP.

## Semantic Interoperability

Nodes exchange Humanitarian Records using the common semantic language defined by HCP.

---

## Organizational Autonomy

Each organization remains responsible for its own infrastructure, operational procedures and humanitarian decisions.

---

## Implementation Independence

Nodes remain free to choose their own:

- programming language;
- database;
- deployment architecture;
- communication technology;
- internal software design.

---

## Local Interpretation

Nodes exchange humanitarian evidence.

Humanitarian Cases remain local.

Interpretation is never synchronized.

---

## Explainability

Whenever a Node produces Correlation Candidates or Humanitarian Cases, the supporting humanitarian evidence should be explainable.

---

## Privacy by Architecture

Implementations should minimize identity information while maximizing humanitarian evidence.

---

## Human Verification

Correlation assists humanitarian decision-making.

People determine reality.

---

# 12. Relationship with Other Specifications

This document defines the architectural role of an HCP Node.

Additional HCP specifications define the behavior implemented by Nodes.

```text
HCP-0000
Architecture and Overview
        │
        ▼
HCP-0001
Humanitarian Record
        │
        ▼
HCP-0002
HCP Node
        │
        ├───────────────┐
        ▼               ▼
HCP-0005          HCP-0009
Node              Node API
Communication
Protocol
        │               │
        └───────┬───────┘
                ▼
          HCP-0010
      Canonical JSON
                │
        ┌───────┼────────┐
        ▼       ▼        ▼
   HCP-0011 HCP-0012 HCP-0013
     Query  Correlation Synchronization
                │
                ▼
          HCP-0015
    Result Presentation
```

Each specification has a distinct responsibility.

- **HCP-0005** defines Node-to-Node communication.
- **HCP-0009** defines the Node API.
- **HCP-0010** defines the Canonical JSON representation.
- **HCP-0011** defines how Nodes query Humanitarian Records.
- **HCP-0012** defines local correlation.
- **HCP-0013** defines synchronization.
- **HCP-0014** defines explainable correlation.
- **HCP-0015** defines local presentation of Humanitarian Cases.

Together, these specifications define how autonomous Nodes remain semantically interoperable while preserving local implementation freedom.

---

# 13. Summary

An HCP Node is an autonomous implementation of the Humanitarian Connection Protocol.

It implements the common semantic language defined by HCP.

Its responsibility is not to determine identity.

Its responsibility is not to determine truth.

Its responsibility is to preserve, exchange and process Humanitarian Records according to the protocol specification.

Different Nodes may implement different protocol capabilities.

Different Nodes may reach different humanitarian interpretations.

They remain interoperable because they exchange the same humanitarian evidence.

Humanitarian Records preserve observations.

Synchronization exchanges observations.

Correlation creates local understanding.

Presentation creates Humanitarian Cases.

Human verification determines reality.

By separating evidence from interpretation, HCP enables independent organizations to collaborate without requiring centralized databases, centralized identity systems or common software platforms.

Autonomous Nodes.

Shared semantics.

Universal humanitarian interoperability.
