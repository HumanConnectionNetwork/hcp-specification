# Humanitarian Connection Protocol (HCP)

> **Connecting Humanity Through Open Standards.**

[![License](https://img.shields.io/badge/license-Apache%202.0-blue.svg)](LICENSE)
![Status](https://img.shields.io/badge/status-Draft-orange)
![Version](https://img.shields.io/badge/HCP-v0.1-lightgrey)

## What is HCP?

The **Humanitarian Connection Protocol (HCP)** is an open specification for representing, exchanging and verifying humanitarian information.

Its purpose is to enable governments, NGOs, volunteers, humanitarian organizations and digital platforms to communicate using a common language during emergencies and humanitarian crises.

HCP **does not define applications**.

HCP defines **how humanitarian information is structured and exchanged**, allowing independent systems to interoperate seamlessly.

Just as HTTP standardized communication on the Web, HCP aims to standardize humanitarian information exchange.

---

# Why HCP?

During large-scale humanitarian emergencies, dozens of organizations create independent tools:

- Telegram bots
- Mobile applications
- Web platforms
- NGO databases
- Government systems
- Volunteer networks

Although all of them pursue the same objective, they usually cannot communicate with one another.

The result is fragmented information, duplicated reports, lost resources and slower humanitarian response.

HCP exists to solve this interoperability problem.

---

# Design Principles

HCP is built around a small set of principles:

- 🌍 Open by Design
- 🤝 Human First
- 🔓 Vendor Neutral
- 🔍 Verifiable
- 🔄 Interoperable
- 🧩 Extensible
- 🔒 Privacy Aware
- ⚡ Simple to Implement

---

# Goals

The protocol is designed to:

- Standardize humanitarian information.
- Reduce duplicated reports.
- Enable interoperability between independent platforms.
- Facilitate verification workflows.
- Improve coordination between organizations.
- Create an open ecosystem rather than a single application.

---

# Non-Goals

HCP is **not**:

- a humanitarian platform
- a donation platform
- a messaging application
- a database
- a blockchain
- an identity provider

Those systems can implement HCP.

HCP simply defines the language they use to communicate.

---

# Current Status

Current Specification:

**HCP v0.1 Draft**

The protocol is currently under active development.

The first version focuses on defining:

- Core Record Format
- JSON Schemas
- Standard Record Types
- Verification Metadata
- Node Interoperability

---

# Repository Structure

```
hcp-specification/

├── README.md

├── docs/

├── specs/

├── schemas/

├── examples/

├── proposals/

└── media/
```

---

# Specifications

Each specification is maintained as an independent document.

| ID | Title | Status |
|----|-------|--------|
| HCP-0000 | Protocol Overview | Draft |
| HCP-0001 | Core Record Format | Draft |
| HCP-0002 | Missing Person Schema | Planned |
| HCP-0003 | Help Request Schema | Planned |
| HCP-0004 | Verification Model | Planned |
| HCP-0005 | Node Synchronization | Planned |

---

# Guiding Philosophy

Humanitarian information should be:

- Portable
- Verifiable
- Interoperable
- Independent of any platform

The protocol belongs to the community, not to any single organization.

---

# Reference Implementation

The official reference implementation is maintained in:

**hcp-node**

This repository contains only the specification.

---

# Governance

HCP is developed as an open standard.

Proposals for changes are discussed publicly through GitHub Issues and Pull Requests.

Future versions of the protocol will be developed collaboratively with the humanitarian and open-source communities.

---

# Contributing

We welcome contributions from:

- Software Engineers
- Humanitarian Organizations
- Emergency Response Teams
- NGOs
- Governments
- Researchers
- Open Source Contributors

Please read:

- CONTRIBUTING.md
- CODE_OF_CONDUCT.md

before contributing.

---

# License

Apache License 2.0

---

# Vision

We believe humanitarian coordination should not depend on a single platform.

It should depend on a common language.

Our goal is to create an open standard that allows every humanitarian application, organization and volunteer network to work together.

**Because helping people should never be limited by incompatible software.**
