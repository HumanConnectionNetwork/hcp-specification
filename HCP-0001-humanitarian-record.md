# HCP-0001
# Humanitarian Record

Version: 0.1 (Draft)

Status: Draft

Depends on:

- Humanitarian Connection Protocol Specification v0.1

---

# 1. Purpose

This specification defines the Humanitarian Record, the fundamental unit of information exchanged within the Humanitarian Connection Protocol (HCP).

Every humanitarian observation exchanged through HCP SHALL be represented as a Humanitarian Record.

The Humanitarian Record is the atomic unit of synchronization across the network.

---

# 2. Definition

A Humanitarian Record is a standardized, immutable JSON document representing a single humanitarian observation made by an identified actor at a specific point in time.

The protocol exchanges Humanitarian Records.

It does not exchange databases.

It does not exchange application state.

It does not exchange mutable objects.

---

# 3. Design Philosophy

HCP follows an event-based architecture.

Each Humanitarian Record represents an observation.

A new observation SHALL generate a new Humanitarian Record.

Existing records MUST NOT be modified.

This guarantees:

- complete history
- distributed synchronization
- traceability
- conflict resistance
- offline operation

---

# 4. Fundamental Principles

## 4.1 Immutability

Once published, a Humanitarian Record SHALL NEVER be modified.

Corrections SHALL be represented by new Humanitarian Records.

---

## 4.2 Atomicity

Each Humanitarian Record represents one humanitarian observation.

A record SHALL NOT contain unrelated observations.

---

## 4.3 Traceability

Every Humanitarian Record becomes part of the permanent humanitarian history.

Historical information MUST remain available.

---

## 4.4 Interoperability

Every compliant implementation SHALL exchange Humanitarian Records using the HCP JSON representation.

---

## 4.5 Technology Independence

Although JSON is the reference serialization format, the conceptual model remains implementation-independent.

---

# 5. Humanitarian Observation

A Humanitarian Record represents an observation made by an actor.

Examples include:

- A hospital reports that a person has been admitted.
- A rescue team reports that a person has been located.
- A volunteer reports that food has been delivered.
- A family reports a missing relative.
- A shelter reports available capacity.

Each observation becomes an independent Humanitarian Record.

---

# 6. Humanitarian Record Identity

Every Humanitarian Record SHALL possess a globally unique identifier (UUID).

The UUID identifies the record itself.

It SHALL NOT represent the identity of a person.

Different records MAY describe the same humanitarian situation.

---

# 7. Humanitarian Record Structure

Every Humanitarian Record SHALL contain the mandatory fields defined by future specifications.

The reference serialization format SHALL be JSON.

Future specifications define:

- required fields
- optional fields
- validation rules
- JSON Schema

---

# 8. Relationships

Humanitarian Records MAY reference other Humanitarian Records.

Relationships allow independent observations to describe the same humanitarian situation without modifying previous records.

Relationship semantics are defined in future specifications.

---

# 9. Record History

The protocol preserves every published Humanitarian Record.

The current understanding of a humanitarian situation is reconstructed from related observations.

The protocol does not replace historical information.

---

# 10. Synchronization

Nodes exchange Humanitarian Records.

Nodes do not exchange complete databases.

Nodes do not synchronize mutable state.

Synchronization consists of transferring immutable Humanitarian Records between compliant nodes.

Synchronization mechanisms are defined in HCP-0003.

---

# 11. Duplicate Records

The protocol does not attempt to prevent duplicate Humanitarian Records.

Independent actors MAY report the same humanitarian situation.

Duplicate detection and record reconciliation are responsibilities of compliant implementations and future HCP specifications.

Original Humanitarian Records MUST remain unchanged.

---

# 12. Offline Operation

Humanitarian Records MAY be created without network connectivity.

Nodes SHALL synchronize records when communication becomes available.

Offline operation is a fundamental design principle of HCP.

---

# 13. Security

Every Humanitarian Record SHOULD preserve information about:

- originating node
- originating actor
- creation timestamp

Future specifications define:

- digital signatures
- integrity verification
- trust models

---

# 14. Compliance

An implementation claiming HCP compatibility MUST:

- create immutable Humanitarian Records
- exchange records using the HCP JSON representation
- preserve record history
- avoid modifying previously synchronized records

---

# 15. Future Work

Future specifications will define:

- JSON Schema
- Mandatory fields
- Record relationships
- Synchronization
- Digital signatures
- Verification
- Record linking
- Conflict resolution
- Node discovery
- APIs

---

# 16. Philosophy

Humanitarian information evolves continuously.

Instead of modifying previous information, HCP preserves every observation as an immutable Humanitarian Record.

The current understanding of any humanitarian situation emerges from the chronological sequence of related Humanitarian Records exchanged across the decentralized HCP network.

The protocol therefore preserves not only humanitarian information, but also the complete history of how that information evolved over time.

---

**End of HCP-0001**
