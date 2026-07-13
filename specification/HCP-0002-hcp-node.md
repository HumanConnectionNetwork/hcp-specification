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

This document defines the concept of an **HCP Node**, the fundamental implementation component of the Humanitarian Connection Protocol.

An HCP Node is an independent implementation capable of creating, querying, exchanging and correlating Humanitarian Records while preserving interoperability with other compatible implementations.

Nodes do not define humanitarian information.

They implement the common language defined by HCP and enable humanitarian observations to be shared across independent systems without requiring centralized infrastructure.

This document establishes the conceptual responsibilities of an HCP Node independently of any programming language, database or deployment architecture.

---

# 1. Introduction

An **HCP Node** is an independent implementation of the Humanitarian Connection Protocol.

Its purpose is to implement the protocol specification and enable humanitarian observations to be represented, queried, exchanged and correlated using the common semantic model defined by HCP.

An HCP Node is implementation-independent.

It is not defined by a specific programming language, database technology, deployment model or communication mechanism.

Instead, an HCP Node is defined by its ability to correctly implement the protocol and maintain interoperability with other compatible HCP implementations.

Clients interact with HCP Nodes.

HCP Nodes interact with other HCP Nodes.

Together they create an interoperable humanitarian network based on shared meaning rather than shared infrastructure.

---

# 2. Purpose

The purpose of an HCP Node is to enable humanitarian interoperability.

Rather than requiring organizations to replace their existing software or adopt a centralized platform, an HCP Node allows them to participate in the HCP ecosystem while preserving their own operational autonomy.

An HCP Node enables independent organizations to:

- create Humanitarian Records
- query Humanitarian Records
- exchange humanitarian observations
- correlate compatible observations
- synchronize humanitarian information

The protocol standardizes communication and meaning.

Each implementation remains free to choose its own technologies and operational model.

---

# 3. Responsibilities

Every HCP Node is responsible for implementing the behavior defined by the HCP specification.

Its primary responsibilities include:

- creating Humanitarian Records
- querying Humanitarian Records
- exchanging Humanitarian Records with compatible HCP Nodes
- preserving observation history
- generating explainable Correlation Candidates
- supporting protocol evolution whenever reasonably possible

An HCP Node is responsible for implementing protocol behavior.

It is not responsible for determining permanent identity.

Identity verification always remains outside the scope of the protocol.

---

# 4. Humanitarian Records

The primary responsibility of an HCP Node is the management of Humanitarian Records.

Humanitarian Records represent independent humanitarian observations concerning living beings affected by humanitarian events.

Current protocol specifications support observations related to:

- Humans
- Animals

Nodes exchange observations.

They do not exchange identities.

Multiple HCP Nodes may independently create Humanitarian Records describing the same humanitarian reality.

Those observations remain independent until compatible implementations determine that they may represent the same humanitarian case through explainable correlation.
---

# 5. Organizational Autonomy

Every HCP Node operates independently.

Organizations remain fully responsible for their own systems, operational policies and humanitarian procedures.

Examples of HCP Node operators include:

- hospitals
- emergency services
- fire departments
- police departments
- humanitarian organizations
- governments
- universities
- community initiatives
- humanitarian foundations
- independent organizations

Each HCP Node independently decides:

- which Humanitarian Records to preserve
- which Humanitarian Records to expose
- which Humanitarian Records to synchronize
- how correlation is implemented
- which internal technologies are used

The protocol intentionally avoids prescribing implementation details.

Organizational autonomy is preserved while interoperability is maintained through compliance with the HCP specification.

---

# 6. HCP Clients

An **HCP Client** is not an HCP Node.

Clients provide user interaction.

Nodes implement protocol behavior.

Typical HCP Clients include:

- Telegram Clients
- WhatsApp Clients
- SMS Clients
- Web Applications
- Mobile Applications
- Desktop Applications
- Future compatible interfaces

Clients allow users to create, search and review Humanitarian Records.

HCP Nodes receive those requests, process them according to the protocol and exchange compatible information with other HCP Nodes when appropriate.

Clients implement user experience.

Nodes implement protocol behavior.

This separation allows different user interfaces to coexist while preserving a common interoperability model.

---

# 7. Communication

HCP Nodes communicate using the protocol defined by the HCP specification.

The protocol defines the structure and meaning of exchanged information.

It does not prescribe the transport mechanism.

Compatible implementations may communicate through technologies such as:

- HTTPS
- local networks
- mesh networks
- satellite communication
- store-and-forward synchronization
- removable media
- offline synchronization
- future communication technologies

The transport layer is intentionally outside the scope of HCP.

Only semantic interoperability is standardized.

This allows the protocol to remain compatible across a wide variety of technological environments.

---

# 8. Correlation

An HCP Node may implement one or more correlation strategies.

The protocol does not prescribe a specific algorithm.

Instead, it defines the semantic information that compatible implementations may use to estimate whether independent Humanitarian Records describe the same humanitarian case.

Correlation may consider evidence such as:

- reported name
- estimated age
- reported location
- observation time
- humanitarian status
- recognition features
- reporting source
- event evolution
- protocol-defined metadata

Correlation estimates probability.

It does not establish identity.

Different implementations may use different correlation methods while remaining fully interoperable through the common semantic model defined by HCP.

---

# 9. Explainability

Whenever an HCP Node provides Correlation Candidates, it should also provide an explanation describing the evidence that contributed to the correlation.

Typical explanations may reference:

- compatible reported names
- compatible estimated ages
- compatible locations
- compatible observation times
- compatible humanitarian status
- similar recognition features
- supporting or conflicting observations

Explainability supports human verification.

It does not replace human judgment.

Transparent correlation improves trust, facilitates humanitarian decision-making and reduces misinformation during humanitarian emergencies.

The detailed Explainable Correlation Model is defined in **HCP-0014**.
---

# 10. Privacy and Security

An HCP Node should exchange only the information necessary to preserve humanitarian interoperability.

Implementations are encouraged to minimize the collection, storage and exchange of personally identifiable information whenever possible.

Whenever equivalent humanitarian value can be achieved through observable characteristics, implementations should prefer observation-based evidence over permanent identifiers.

Security mechanisms remain implementation-specific.

Each organization may define its own authentication, authorization, encryption and operational security policies.

The protocol standardizes humanitarian interoperability rather than operational security.

Additional requirements are defined in:

- **HCP-0020 — Security Model**
- **HCP-0021 — Privacy and Data Minimization**

---

# 11. Version Compatibility

Every HCP Node should expose the protocol version it implements.

Version information allows compatible implementations to negotiate supported capabilities and maintain interoperability as the protocol evolves.

Whenever reasonably possible, newer HCP implementations should preserve backward compatibility with previous protocol versions.

Maintaining compatibility reduces fragmentation and facilitates gradual protocol adoption across independent organizations.

Protocol evolution should prioritize interoperability over unnecessary breaking changes.

---

# 12. Conceptual Architecture

The following diagram illustrates the conceptual role of an HCP Node within the Human Connection Network ecosystem.

```text
                 HCP Clients
      (Telegram, SMS, Web, Mobile,
       Desktop, APIs and others)

                    │
                    ▼

             ┌─────────────────┐
             │    HCP Node      │
             └─────────────────┘

      • Create Humanitarian Records

      • Query Humanitarian Records

      • Correlate Observations

      • Explain Correlation

      • Synchronize with HCP Nodes

                    │
                    ▼

          Independent HCP Nodes

                    │
                    ▼

      Shared Humanitarian Meaning
```

This architecture is conceptual.

The specification defines protocol behavior.

It does not prescribe internal software architecture or deployment models.

---

# 13. Design Principles

Every HCP Node should preserve the following principles.

## Semantic Interoperability

Exchange Humanitarian Records using the common semantic model defined by HCP.

---

## Organizational Autonomy

Each organization remains responsible for its own systems, operational procedures and humanitarian decisions.

---

## Infrastructure Independence

Implementations remain free to choose their own programming languages, databases, communication technologies and deployment architectures.

---

## Explainability

Correlation should be transparent and understandable.

Whenever possible, implementations should explain why observations appear related.

---

## Privacy by Design

Collect and exchange only the information necessary to support humanitarian interoperability.

---

## Human Verification

Correlation supports humanitarian decision-making.

Final verification always belongs to people and responsible institutions.

---

## Offline-first

Implementations should support environments with limited, intermittent or delayed connectivity whenever practical.

---

## Long-term Compatibility

Implementations should preserve interoperability across protocol versions whenever reasonably possible.

---

# 14. Relationship with Other Specifications

This document defines the conceptual behavior of an HCP Node.

Additional HCP specifications define complementary aspects of node behavior.

- **HCP-0001** defines the Humanitarian Record.
- **HCP-0005** defines the Node Communication Protocol.
- **HCP-0009** defines the Node API.
- **HCP-0010** defines the Canonical HCP JSON Representation.
- **HCP-0011** defines the Query Model.
- **HCP-0012** defines the Correlation Model.
- **HCP-0013** defines the Synchronization Model.
- **HCP-0014** defines the Explainable Correlation Model.

Together, these specifications define how HCP Nodes create, exchange, query, synchronize and correlate Humanitarian Records while preserving interoperability across independent implementations.

---

# 15. Summary

An HCP Node is an independent implementation of the Humanitarian Connection Protocol.

Its responsibility is not to identify people.

Its responsibility is to implement the protocol and enable humanitarian observations to be represented, exchanged, queried and correlated using a common semantic model.

HCP Clients connect people.

HCP Nodes connect humanitarian observations.

Together they allow independent systems to understand the same humanitarian reality without requiring shared infrastructure or centralized identity management.

The HCP Node is the implementation layer of the Humanitarian Connection Protocol.

It transforms the protocol specification into humanitarian interoperability.

By preserving independent observations rather than centralized identity records, HCP improves interoperability while respecting organizational autonomy.
