# HCP-0002

# HCP Node

Version: 0.2 (Draft)

Status: Draft

Category: Core Specification

Project: Human Connection Network (HCN)

License: Apache-2.0

Last Updated: 2026-07-07

Depends On:

- HCP-0000 Overview
- HCP-0001 Humanitarian Record

---

# 1. Introduction

An HCP Node is an independent system that implements the Humanitarian Connection Protocol.

Nodes exchange Humanitarian Records with other compatible nodes using the HCP specification.

Nodes are responsible for preserving, querying and synchronizing humanitarian observations.

Clients interact with nodes.

Nodes interact with other nodes.

---

# 2. Purpose

The purpose of an HCP Node is to make humanitarian observations available in a standardized and interoperable manner.

A node does not own the protocol.

A node does not own humanitarian information.

A node simply participates in a decentralized humanitarian network.

---

# 3. Responsibilities

An HCP Node should be capable of:

- Creating Humanitarian Records.
- Querying Humanitarian Records.
- Synchronizing observations with other compatible nodes.
- Preserving observation history.
- Providing explainable correlation candidates.
- Remaining interoperable with future HCP versions whenever possible.

---

# 4. Humanitarian Records

Nodes exchange Humanitarian Records.

A Humanitarian Record represents an observation about a living being during a humanitarian situation.

Supported subject types include:

- Human
- Animal

Nodes should not attempt to identify people.

Nodes exchange observations.

Human verification remains outside the protocol.

---

# 5. Node Independence

Every node remains independent.

Examples include:

- Hospital
- Fire Department
- Police
- University
- NGO
- Government
- Community
- Humanitarian Foundation
- Independent Organization

Each node decides:

- Which observations to preserve.
- Which observations to expose.
- Which observations to synchronize.
- Which internal database technology to use.

The protocol does not impose implementation details.

---

# 6. Clients

Clients are not nodes.

Clients are user interfaces that communicate with nodes.

Examples:

- Telegram Bot
- WhatsApp Bot
- SMS Client
- Web Client
- Mobile Application
- Desktop Application

Clients create and query Humanitarian Records.

Nodes store and synchronize them.

---

# 7. Communication

Nodes exchange information using HCP.

The transport mechanism is implementation-specific.

Examples include:

- HTTPS
- Local Network
- Mesh Networks
- Satellite Links
- Store-and-forward synchronization
- Offline synchronization

The protocol defines interoperability.

It does not mandate a transport layer.

---

# 8. Correlation

Nodes may execute correlation algorithms.

Correlation attempts to estimate whether multiple observations describe the same humanitarian event.

Recommended variables include:

- Temporal proximity
- Geographic proximity
- Reported name
- Estimated age
- Event evolution
- Source
- Description

Correlation should produce probabilities.

Never certainty.

---

# 9. Explainability

Whenever correlation is provided, nodes should also provide an explanation.

Examples:

✓ Similar reported name

✓ Compatible estimated age

✓ Same geographic area

✓ Compatible reporting time

✗ Different source

Explainability improves transparency and human verification.

---

# 10. Privacy

Nodes should exchange only the information necessary for humanitarian interoperability.

Nodes are encouraged to minimize personally identifiable information whenever possible.

HCP prioritizes observations over identities.

---

# 11. Version Compatibility

Nodes should expose the HCP version they implement.

Whenever possible, newer nodes should remain compatible with previous protocol versions.

Backward compatibility increases interoperability.

---

# 12. Example Architecture

```text
Telegram Client
        │
        │
Web Client
        │
        │
SMS Client
        │
        ▼
────────────────────────────

        HCP Node

────────────────────────────

Create Record

Query Record

Correlation

Synchronization

────────────────────────────

        │
        ▼

Other HCP Nodes
```

---

# 13. Design Principles

Every HCP Node should preserve the following principles:

- Decentralization
- Interoperability
- Explainability
- Simplicity
- Human Verification
- Long-term compatibility
- Privacy by Design
- Offline-first whenever possible

---

# 14. Summary

An HCP Node is an independent implementation of the Humanitarian Connection Protocol.

Its responsibility is not to identify people.

Its responsibility is to preserve, exchange and correlate humanitarian observations about living beings.

Clients connect people.

Nodes connect observations.

Together they enable decentralized humanitarian interoperability.
