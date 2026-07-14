# HCP-0001

# Humanitarian Record

Version: 0.2 (Draft)

Status: Draft

Category: Core Specification

Project: Human Connection Network (HCN)

License: Apache-2.0

Last Updated: 2026-07-13

Depends On:

- HCP-0000 — Architecture and Overview

Replaces:
None

Replaced By:
None

---

# Abstract

This document defines the Humanitarian Record, the fundamental semantic unit of the Humanitarian Connection Protocol (HCP).

A Humanitarian Record is the canonical representation of a single Humanitarian Observation.

It represents humanitarian evidence reported by a person, institution or system during a humanitarian event.

Humanitarian Records are intentionally simple, portable, interoperable and implementation-independent.

They enable independent implementations to exchange humanitarian observations while preserving organizational autonomy, technological independence and local interpretation.

This document establishes the conceptual foundation upon which Canonical JSON, synchronization, queries, correlation and presentation are built.

---

# 1. Introduction

The Humanitarian Record is the fundamental semantic unit of the Humanitarian Connection Protocol.

It provides a standardized representation of humanitarian observations that can be exchanged and understood by independent HCP implementations.

A Humanitarian Record represents humanitarian evidence.

It does not represent:

- an identity;
- a person;
- a medical history;
- a humanitarian case;
- verified truth.

Instead, it records what was observed, received or documented at a specific moment in time using the common semantic language defined by HCP.

Multiple Humanitarian Records may describe the same humanitarian reality from different perspectives.

Those observations remain independent.

Only local correlation may later suggest that they describe the same Humanitarian Case.

Humanitarian Records preserve evidence.

Humanitarian Cases represent interpretation.

---

# 2. Humanitarian Observation

A Humanitarian Observation exists independently of HCP.

It represents information observed, received or documented during a humanitarian event.

Observations exist regardless of whether HCP is used.

The protocol does not create observations.

Instead, it provides a canonical representation that allows observations to be exchanged between independent implementations.

Every Humanitarian Observation represents a single humanitarian event witnessed, reported or documented by a person, institution or system.

Examples include:

- a volunteer reports seeing a missing child;
- a hospital admits an unidentified patient;
- a shelter registers a displaced family;
- a firefighter reports rescuing an injured person;
- a citizen reports finding a lost dog.

Each observation may generate one Humanitarian Record.

Independent organizations may observe the same humanitarian situation without communicating with one another.

Rather than attempting to eliminate these independent observations, HCP preserves them as separate pieces of humanitarian evidence.

This separation improves transparency, explainability and long-term interoperability.

---

# 3. Purpose

The purpose of a Humanitarian Record is to enable humanitarian interoperability.

Rather than requiring organizations to exchange databases or adopt common software, HCP enables them to exchange humanitarian observations through a shared semantic model.

Because every implementation represents observations consistently, Humanitarian Records created by different organizations can later be synchronized, queried and correlated while preserving organizational autonomy.

The protocol therefore standardizes humanitarian meaning rather than software architecture.

Evidence can be exchanged universally.

Interpretation remains local.

---

# 4. Design Principles

Every Humanitarian Record should preserve the following architectural principles.

## Observation-Based

A Humanitarian Record represents a humanitarian observation rather than verified reality.

It records what was observed at the time of reporting.

Future observations may confirm, refine or contradict previous observations.

Independent observations should always be preserved.

---

## Evidence-Oriented

Humanitarian Records provide humanitarian evidence.

They intentionally avoid making assumptions about identity or certainty.

Their purpose is to support future humanitarian understanding through explainable correlation.

---

## Correlation-Oriented

Humanitarian Records are designed to maximize the quality of future correlation.

Correlation evaluates the consistency of multiple independent observations.

No individual field should ever be interpreted as definitive proof of identity.

Every observation contributes evidence that may strengthen or weaken a future correlation.

---

## Independent

Every Humanitarian Record exists independently.

Observations should never overwrite one another.

As humanitarian situations evolve, new observations generate new Humanitarian Records.

Previous observations remain part of the humanitarian history.

---

## Infrastructure Independent

Humanitarian Records are implementation-independent.

Any compatible HCP Node may create, store, synchronize and exchange Humanitarian Records using its own technologies.

Interoperability is achieved through shared semantics rather than shared software.

---

## Minimal

Humanitarian Records should contain only the information necessary to support humanitarian interoperability.

Implementations should minimize unnecessary personal information whenever possible.

Privacy and interoperability are strengthened through data minimization.
---
# 5. Correlation Evidence

The primary purpose of a Humanitarian Record is to provide humanitarian evidence that may contribute to future correlation.

Rather than relying on permanent identifiers, HCP encourages implementations to evaluate the overall consistency of multiple independent observations.

Typical correlation evidence may include:

- Reported Label;
- estimated age;
- reported location;
- observation time;
- Event Type;
- reporting source;
- Recognition Features;
- protocol-defined metadata.

No individual attribute should ever be interpreted as definitive proof of identity.

Correlation emerges from the combined consistency of multiple independent observations.

Different HCP implementations may apply different correlation strategies or weighting algorithms while remaining fully interoperable.

Because correlation is a local process, different implementations may reach different conclusions from the same Humanitarian Records.

This behavior is expected.

---

# 6. Recognition Features

Recognition Features are one of the most valuable forms of humanitarian evidence available for correlation.

They describe directly observable characteristics recorded during a humanitarian observation.

Recognition Features represent observations rather than inferred attributes.

Examples for persons include:

- clothing;
- colors;
- tattoos;
- scars;
- glasses;
- backpacks;
- hairstyle;
- beard;
- mobility aids;
- visible injuries.

Examples for animals include:

- collar;
- harness;
- coat color;
- visible markings;
- scars;
- injuries;
- tail characteristics;
- ear shape;
- distinctive physical features.

Recognition Features should remain concise, objective and directly observable.

Implementations should avoid subjective opinions, assumptions or speculative descriptions whenever possible.

Recognition Features improve humanitarian correlation while minimizing dependence on permanent identifiers.

---

# 7. Humanitarian Record Lifecycle

Humanitarian Records are immutable.

Each Humanitarian Record represents one humanitarian observation recorded at a specific moment in time.

As humanitarian situations evolve, new observations generate new Humanitarian Records.

Previous Humanitarian Records are never modified.

This approach preserves:

- observation history;
- explainability;
- transparency;
- long-term interoperability.

The complete lifecycle governing Humanitarian Records is defined in **HCP-0016 — Humanitarian Record Lifecycle**.

---

# 8. Identity

Humanitarian Records intentionally separate humanitarian observations from permanent identity.

Identity verification remains an essential human responsibility.

Families, hospitals, emergency responders and other responsible organizations may eventually confirm that multiple observations refer to the same individual.

The protocol itself does not attempt to establish identity as a technical certainty.

Instead, it provides structured humanitarian evidence that may contribute to human verification.

Reported Labels, estimated ages and similar attributes are treated as reported observations rather than unique identifiers.

HCP minimizes identity.

HCP maximizes humanitarian evidence.

By separating observations from identity, the protocol improves interoperability while reducing unnecessary dependence on centralized identity systems.

---

# 9. Interoperability

Every compliant HCP implementation exchanges Humanitarian Records using the Canonical HCP JSON Representation defined in **HCP-0010**.

Implementations remain free to choose:

- any programming language;
- any database technology;
- any deployment architecture;
- any communication infrastructure.

The protocol standardizes the semantic meaning of Humanitarian Records rather than their technical implementation.

Shared meaning replaces shared infrastructure.

This allows independent HCP Nodes to exchange and understand humanitarian observations while preserving complete technological independence.

Semantic interoperability remains the primary interoperability objective of HCP.

---

# 10. Security and Privacy

Humanitarian Records should contain only the information necessary to support humanitarian interoperability and explainable correlation.

Implementations should minimize the collection and exchange of personally identifiable information whenever possible.

Whenever equivalent humanitarian value can be achieved through observable evidence, implementations should prefer observations over permanent identifiers.

Privacy is preserved primarily through protocol architecture rather than through infrastructure.

Likewise, interoperability should never require excessive exposure of personal information.

HCP seeks to balance humanitarian usefulness, privacy protection and long-term interoperability.

Additional requirements are defined in:

- **HCP-0020 — Security Model**
- **HCP-0021 — Privacy and Data Minimization**
- ---
# 11. Relationship with Other Specifications

The Humanitarian Record is the central semantic object of the Humanitarian Connection Protocol.

All subsequent HCP specifications extend, process or exchange Humanitarian Records while preserving their original humanitarian meaning.

The relationship between this specification and the remainder of the HCP Core is illustrated below.

```text
HCP-0000
Architecture and Overview
        │
        ▼
HCP-0001
Humanitarian Record
        │
        ├───────────────┐
        ▼               ▼
HCP-0006          HCP-0008
Observation       Event Type
Model             Model
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
                │
                ▼
      Humanitarian Case
```

Each specification has a distinct responsibility.

- **HCP-0000** defines the architectural vision of the protocol.
- **HCP-0001** defines the Humanitarian Record.
- **HCP-0006** defines the Observation Model.
- **HCP-0008** defines humanitarian semantic meaning through Event Types.
- **HCP-0010** defines the Canonical JSON representation.
- **HCP-0011** defines how humanitarian evidence is queried.
- **HCP-0012** defines how observations are correlated.
- **HCP-0013** defines synchronization between independent Nodes.
- **HCP-0015** defines how Humanitarian Cases are presented locally.

Together, these specifications establish a complete semantic model while maintaining a clear separation between observations, interpretation and presentation.

---

# 12. Summary

The Humanitarian Record is the fundamental semantic unit of the Humanitarian Connection Protocol.

It is the canonical representation of a single Humanitarian Observation.

Humanitarian Records preserve humanitarian evidence.

They do not represent identities.

They do not represent Humanitarian Cases.

They do not establish truth.

Instead, they provide a common semantic language that allows independent implementations to exchange humanitarian observations while preserving organizational autonomy and technological independence.

Every Humanitarian Record remains an independent observation.

Synchronization exchanges Humanitarian Records.

Correlation evaluates Humanitarian Records.

Presentation creates Humanitarian Cases.

Human verification determines reality.

By separating evidence from interpretation, HCP enables humanitarian collaboration without requiring centralized databases, centralized identity systems or common software platforms.

Humanitarian Records preserve observations.

Shared observations enable semantic interoperability.

Semantic interoperability enables humanitarian collaboration.
