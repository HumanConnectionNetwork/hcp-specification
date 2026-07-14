# HCP-0018

# Search Protocol

Version: 0.3 (Draft)

Status: Draft

Category: Core Specification

Project: Human Connection Network (HCN)

License: Apache-2.0

Last Updated: 2026-07-13

Depends On:

- HCP-0002 — HCP Node
- HCP-0005 — Node Communication Protocol
- HCP-0011 — Query Model
- HCP-0012 — Correlation Model
- HCP-0013 — Synchronization Model

Replaces:
None

Replaced By:
None

---

# Abstract

This document defines the Search Protocol of the Humanitarian Connection Protocol (HCP).

The Search Protocol describes how HCP Nodes retrieve Humanitarian Records that may contribute humanitarian evidence for a humanitarian search.

Search retrieves Humanitarian Records.

It never retrieves identities.

It never creates humanitarian understanding.

Correlation, explainability and presentation occur only after humanitarian evidence has been collected.

The protocol standardizes the semantic behavior of humanitarian search.

It does not prescribe search algorithms, transport technologies or implementation architectures.

---

# 1. Introduction

Humanitarian emergencies frequently require humanitarian evidence distributed across multiple independent HCP Nodes.

Hospitals, shelters, emergency responders, humanitarian organizations and volunteers may each possess different Humanitarian Records describing related humanitarian situations.

The Search Protocol defines how HCP Nodes retrieve those Humanitarian Records using standardized Queries.

Search retrieves humanitarian evidence.

It never evaluates humanitarian compatibility.

It never generates Correlation Candidates.

It never generates Humanitarian Cases.

Those responsibilities belong to later stages of the protocol.

Search exists exclusively to retrieve humanitarian evidence.

---

# 2. Purpose

The purpose of the Search Protocol is to define the semantic principles governing humanitarian search within HCP.

Search enables HCP Nodes to:

- execute humanitarian Queries;
- retrieve Humanitarian Records;
- collect humanitarian evidence;
- discover distributed humanitarian observations.

The protocol intentionally separates humanitarian search from humanitarian interpretation.

Search retrieves Humanitarian Records.

Correlation creates humanitarian understanding.

The Search Protocol answers one fundamental question:

> **How are Humanitarian Records retrieved?**

---

# 3. Design Principles

Every Search Protocol follows the architectural principles of HCP.

---

## Evidence-Based

Search retrieves Humanitarian Records containing humanitarian evidence.

It never retrieves identities.

---

## Local First

Every humanitarian search begins locally.

Distributed search extends local search.

It never replaces it.

---

## Progressive

Search results may improve as additional Humanitarian Records become available through synchronization.

Search therefore represents the humanitarian evidence currently available rather than all humanitarian evidence that may eventually exist.

---

## Decentralized

No central search authority exists.

Every HCP Node remains autonomous.

---

## Stateless

Each Query is evaluated independently.

Persistent search sessions are never required.

---

## Transport Independent

Search semantics remain identical regardless of the communication technology used.

---

## Fault Tolerant

Unavailable Nodes should never prevent humanitarian search from completing.

Partial humanitarian evidence remains valuable.

---

## Implementation Independent

Every implementation remains free to optimize search execution.

The protocol standardizes humanitarian search behavior.

It never standardizes implementation techniques.

---

# 4. Search Philosophy

Search retrieves humanitarian evidence.

Interpretation always remains local.

The Humanitarian Connection Protocol intentionally separates humanitarian evidence retrieval from humanitarian interpretation.

Humanitarian understanding emerges only after correlation evaluates the available Humanitarian Records.

The fundamental philosophy of humanitarian search is:

**Search retrieves Humanitarian Records.**

**Correlation creates humanitarian understanding.**

**Clients communicate Humanitarian Cases.**

**People verify reality.**

---

# 5. Search Boundaries

The Search Protocol intentionally defines strict architectural boundaries.

Search never:

- performs humanitarian correlation;
- generates Correlation Candidates;
- generates Humanitarian Cases;
- explains humanitarian reasoning;
- performs presentation;
- verifies reality.

Search retrieves Humanitarian Records only.

Everything else remains the responsibility of subsequent protocol stages.

---

# 6. Search Pipeline

Every humanitarian search follows the same conceptual sequence.

```text
Client

        │

        ▼

Query

        │

        ▼

Search

        │

        ▼

Humanitarian Records

        │

        ▼

Correlation

        │

        ▼

Correlation Candidates

        │

        ▼

Humanitarian Reasoning

        │

        ▼

Humanitarian Cases

        │

        ▼

Presentation
```

The Search Pipeline intentionally separates humanitarian evidence retrieval from humanitarian interpretation.

Search retrieves Humanitarian Records.

Correlation evaluates humanitarian evidence.

Explainability communicates humanitarian reasoning.

Presentation communicates Humanitarian Cases.

---

# 7. Search Scope

Implementations may execute humanitarian searches using different operational scopes.

Illustrative search scopes include:

- local HCP Node;
- selected peer Nodes;
- regional humanitarian federations;
- national humanitarian federations;
- global humanitarian federations.

Search Scope determines where Humanitarian Records are retrieved.

It never changes the semantic behavior of humanitarian search.

---

# 8. Local Search

Every humanitarian search begins within the local HCP Node.

The implementation first evaluates the Humanitarian Records already available locally.

If sufficient humanitarian evidence is available, distributed search may be unnecessary.

Local-first search minimizes latency, reduces network traffic and supports offline-first humanitarian operation.

---

# 9. Distributed Search

When permitted, an HCP Node may forward the Query to compatible peer Nodes.

Illustrative example:

```text
Client

        │

        ▼

Node A

      ╱ │ ╲

     ▼  ▼  ▼

Node B

Node C

Node D
```

Each receiving Node independently executes the Query against its own Humanitarian Records.

Every Node returns only the Humanitarian Records available within its own repository.

Distributed search never centralizes humanitarian information.

It distributes humanitarian discovery.
---
# 10. Query Propagation

Implementations should avoid unlimited propagation of humanitarian Queries.

Typical propagation controls include:

- maximum hop count;
- time-to-live (TTL);
- trusted peer restrictions;
- geographic boundaries;
- organizational boundaries.

Propagation strategies improve scalability while preserving decentralized operation.

Propagation policies remain entirely implementation-specific.

---

# 11. Result Collection

Each participating HCP Node returns the Humanitarian Records matching the received Query.

Returned Humanitarian Records remain completely independent humanitarian observations.

Nodes never:

- merge Humanitarian Records;
- modify Humanitarian Records;
- generate Humanitarian Cases;
- interpret humanitarian evidence.

Every returned Humanitarian Record preserves exactly the humanitarian observation originally published.

Search concludes once humanitarian evidence has been collected.

---

# 12. Correlation After Search

After humanitarian evidence has been collected, responsibility transfers to the local Correlation Model.

From this point onward the HCP Node may execute:

- humanitarian correlation;
- Correlation Candidate generation;
- humanitarian reasoning;
- Humanitarian Case construction;
- result presentation.

These operations remain completely independent from the Search Protocol.

Search retrieves evidence.

Correlation creates humanitarian understanding.

Presentation communicates humanitarian understanding.

---

# 13. Progressive Search

Humanitarian search is inherently progressive.

Additional Humanitarian Records may become available because:

- synchronization occurred;
- additional HCP Nodes became reachable;
- new humanitarian observations were published.

Consequently, executing the same Query at different moments may legitimately produce different Humanitarian Records.

Search results evolve because humanitarian evidence evolves.

The Search Protocol always reflects the humanitarian evidence currently available.

---

# 14. Query Completion

A humanitarian search may complete under different operational conditions.

Illustrative completion conditions include:

- all selected HCP Nodes have responded;
- the configured timeout has expired;
- the maximum search scope has been reached;
- local operational policies terminate the search.

Partial humanitarian evidence remains valuable.

Future searches may retrieve additional Humanitarian Records.

---

# 15. Fault Tolerance

Distributed humanitarian environments naturally experience communication failures.

Unavailable HCP Nodes should never prevent humanitarian search from completing.

Search proceeds using the Humanitarian Records successfully retrieved.

Temporary communication failures reduce search completeness.

They never reduce semantic interoperability.

---

# 16. Privacy and Security

Every HCP Node determines which Humanitarian Records are available for search according to its local operational policies.

Implementations may restrict searchable Humanitarian Records based upon:

- organizational policies;
- humanitarian context;
- local legislation;
- access permissions.

Incoming Queries should also be validated before execution.

Typical validation includes:

- protocol compatibility;
- Query integrity;
- authorization policies;
- supported protocol version.

Security mechanisms remain implementation-specific.

They never modify humanitarian semantics.

---

# 17. Rate Limiting

Implementations are encouraged to protect humanitarian search services against abusive or excessive querying.

Illustrative mechanisms include:

- request quotas;
- authentication;
- query throttling;
- caching;
- trusted peer prioritization.

Rate limiting protects operational stability.

It should never alter the semantic behavior of humanitarian search.

---

# 18. Transport Independence

The Search Protocol intentionally avoids prescribing communication technologies.

Compatible implementations may execute humanitarian searches using:

- HTTPS;
- gRPC;
- Message Queues;
- MQTT;
- WebSockets;
- offline synchronization;
- future communication technologies.

Regardless of transport technology, humanitarian search semantics remain identical.

---

# 19. Version Compatibility

HCP Nodes should advertise the protocol versions they support.

Search operations should use only features compatible with every participating Node.

Whenever reasonably possible, backward compatibility should be preserved.

Version negotiation affects implementation compatibility.

It never affects humanitarian semantics.

---

# 20. Relationship with Other Specifications

The Search Protocol defines how Humanitarian Records are retrieved using standardized Queries.

Complementary specifications define the remaining stages of humanitarian interoperability.

```text
Client

        │

        ▼

Query

        │

        ▼

Search

        │

        ▼

Humanitarian Records

        │

        ▼

Correlation

        │

        ▼

Correlation Candidates

        │

        ▼

Humanitarian Reasoning

        │

        ▼

Humanitarian Cases

        │

        ▼

Presentation

        │

        ▼

Human Verification
```

Each specification has a distinct responsibility.

- **HCP-0002** defines the HCP Node.
- **HCP-0005** defines the Node Communication Protocol.
- **HCP-0011** defines the Query Model.
- **HCP-0012** defines the Correlation Model.
- **HCP-0013** defines the Synchronization Model.
- **HCP-0014** defines the Explainable Correlation Model.
- **HCP-0015** defines the Result Presentation Model.

Together, these specifications define how humanitarian evidence is searched, retrieved, interpreted and communicated while preserving decentralization and implementation independence.

---

# 21. Summary

The Search Protocol defines the semantic principles governing humanitarian search within HCP.

Search retrieves Humanitarian Records.

It never retrieves identities.

It never performs humanitarian correlation.

It never creates humanitarian understanding.

Humanitarian understanding begins only after correlation evaluates the collected Humanitarian Records.

Different HCP Nodes may implement completely different search technologies while preserving identical humanitarian semantics.

By separating humanitarian search from humanitarian interpretation, HCP preserves scalability, implementation independence and long-term interoperability.

The Search Protocol reinforces one of the central architectural principles of HCP:

**Search retrieves Humanitarian Records.**

**Correlation evaluates humanitarian evidence.**

**Humanitarian Reasoning explains interpretation.**

**Clients communicate Humanitarian Cases.**

**People verify reality.**
