# HCP-0005
# Record Linking

Version: 0.1 (Draft)

Status: Draft

Depends on:

- Humanitarian Connection Protocol Specification v0.1
- HCP-0001 Humanitarian Record
- HCP-0002 HCP Node
- HCP-0003 Synchronization
- HCP-0004 Node Identity

---

# 1. Purpose

This specification defines how independent Humanitarian Records MAY be associated to represent the same humanitarian situation.

Record Linking enables decentralized reconciliation without modifying existing Humanitarian Records.

---

# 2. Definition

Record Linking is the process of establishing an explicit relationship between two or more Humanitarian Records.

A link does not merge records.

A link does not delete records.

A link does not modify records.

It simply states that the linked records are believed to describe the same humanitarian situation or are otherwise related.

---

# 3. Design Principles

Record Linking SHALL satisfy the following principles:

- Non-destructive
- Immutable
- Traceable
- Independent
- Technology-neutral

---

# 4. Why Record Linking Exists

In humanitarian emergencies, multiple independent actors frequently report the same situation.

Examples include:

- A hospital admits an injured person.
- A family reports the same person as missing.
- A rescue team reports that the person has been located.

Each observation produces an independent Humanitarian Record.

Rather than attempting to prevent duplicate records, HCP allows them to coexist and be linked.

---

# 5. Link Creation

A Record Link MAY be created by:

- an HCP Node;
- an authorized operator;
- an automated system;
- an artificial intelligence system;
- any future implementation capable of establishing relationships.

The protocol does not prescribe how links are discovered.

It only standardizes how they are represented.

---

# 6. Link Identity

Every Record Link SHALL possess its own unique identifier.

A Record Link is itself an immutable object within the protocol.

Future specifications MAY represent Record Links as specialized Humanitarian Records.

---

# 7. Link Evidence

A Record Link SHOULD preserve contextual information supporting the relationship.

Examples include:

- matching names;
- similar locations;
- compatible timestamps;
- corroborating observations;
- external verification.

The protocol does not define mandatory matching criteria.

---

# 8. Confidence

A Record Link MAY include a confidence level assigned by the creating implementation.

Confidence values are implementation-specific.

The protocol does not prescribe any scoring methodology.

---

# 9. Record Preservation

Creating a Record Link SHALL NEVER modify the linked Humanitarian Records.

All original observations remain available.

This guarantees complete historical traceability.

---

# 10. Distributed Operation

Record Links SHALL propagate through synchronization in the same manner as Humanitarian Records.

Nodes MAY accept, reject or ignore received links according to local trust policies.

---

# 11. Conflict Tolerance

Different nodes MAY create different links for the same Humanitarian Records.

The protocol permits multiple independent interpretations.

Future specifications define trust and conflict resolution mechanisms.

---

# 12. Future Work

Future specifications will define:

- link serialization;
- relationship types;
- trust models;
- graph construction;
- confidence exchange;
- automatic reconciliation.

---

# 13. Philosophy

Humanitarian reality is often fragmented.

Different actors observe different parts of the same situation.

Instead of forcing a single authoritative version, HCP preserves every observation and allows relationships to emerge over time.

Knowledge grows by adding relationships, never by erasing history.

---

**End of HCP-0005**
