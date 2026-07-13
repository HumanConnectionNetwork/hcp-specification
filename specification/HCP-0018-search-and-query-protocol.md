# HCP-0018

# Search and Query Protocol

Version: 0.2 (Draft)

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

This document defines the Search and Query Protocol of the Humanitarian Connection Protocol (HCP).

The Search and Query Protocol describes how HCP Nodes execute humanitarian searches using the Query Model defined by **HCP-0011**.

Search retrieves humanitarian evidence.

It never retrieves identities.

The purpose of search is to collect compatible Humanitarian Records that may contribute to humanitarian understanding.

Correlation and result presentation occur only after humanitarian evidence has been collected.

The protocol standardizes the semantic behavior of humanitarian search.

It does not prescribe transport technologies or search algorithms.

---

# 1. Introduction

Humanitarian emergencies frequently require information distributed across multiple independent HCP Nodes.

Hospitals, shelters, emergency responders and humanitarian organizations may each possess different Humanitarian Records describing the same humanitarian situation.

The Search and Query Protocol defines how HCP Nodes execute humanitarian searches using standardized Queries.

Search retrieves Humanitarian Records.

It does not generate Correlation Candidates.

It does not generate Humanitarian Cases.

Those responsibilities belong to subsequent stages of the protocol.

The Search and Query Protocol exists solely to retrieve humanitarian evidence.

---

# 2. Purpose

The purpose of the Search and Query Protocol is to define the semantic principles governing humanitarian search within HCP.

Search enables HCP Nodes to:

- execute humanitarian Queries;
- retrieve compatible Humanitarian Records;
- collect humanitarian evidence from multiple Nodes;
- support decentralized humanitarian discovery.

The protocol intentionally separates humanitarian search from humanitarian interpretation.

Search retrieves evidence.

Correlation creates humanitarian understanding.

---

# 3. Design Principles

Every Search and Query Protocol follows the fundamental architectural principles of HCP.

---

## Evidence-Based

Search retrieves Humanitarian Records.

It never retrieves identities.

---

## Local First

Every humanitarian search begins within the local HCP Node.

Distributed search extends local search.

It never replaces it.

---

## Decentralized

No central search authority exists.

Every HCP Node remains autonomous.

---

## Stateless

Each Query is evaluated independently.

Search does not require persistent query sessions.

---

## Transport Independent

Search semantics remain identical regardless of the communication technology used.

---

## Fault Tolerant

Unavailable Nodes should never prevent humanitarian search from completing.

Partial humanitarian evidence remains valuable.

---

## Implementation Independent

Every HCP implementation remains free to optimize search execution.

The protocol standardizes humanitarian search behavior.

It does not standardize implementation techniques.

---

# 4. Search Philosophy

Search retrieves humanitarian evidence.

It does not establish humanitarian understanding.

The Humanitarian Connection Protocol intentionally separates evidence retrieval from humanitarian interpretation.

Humanitarian understanding emerges only after correlation has evaluated the available Humanitarian Records.

The fundamental philosophy of humanitarian search is:

**Search retrieves humanitarian evidence.**

**Correlation creates humanitarian understanding.**

**Clients communicate Humanitarian Cases.**

**People verify reality.**
---

# 5. Search Pipeline

Every humanitarian search follows the same conceptual sequence.

```text
Client

        │

        ▼

Query

        │

        ▼

Local Search

        │

        ▼

Distributed Search (optional)

        │

        ▼

Collect Humanitarian Records

        │

        ▼

Correlation

        │

        ▼

Result Presentation

        │

        ▼

Humanitarian Cases
```

The Search Pipeline separates humanitarian evidence retrieval from humanitarian interpretation.

Search retrieves Humanitarian Records.

Correlation evaluates humanitarian evidence.

Presentation communicates Humanitarian Cases.

---

# 6. Search Scope

Implementations may execute humanitarian searches using different scopes according to local operational policies.

Typical search scopes include:

- local HCP Node;
- selected peer Nodes;
- regional humanitarian networks;
- national humanitarian networks;
- global humanitarian networks.

The selected scope affects where Humanitarian Records are searched.

It never changes the semantic behavior of the protocol.

---

# 7. Local Search

Every humanitarian search begins locally.

The HCP Node first evaluates the Humanitarian Records already available within its own repository.

If local humanitarian evidence sufficiently satisfies the Query, the implementation may decide that no distributed search is necessary.

Local search minimizes latency and reduces unnecessary network traffic.

---

# 8. Distributed Search

When enabled, an HCP Node may forward the Query to compatible peer Nodes.

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

Each Node returns only humanitarian evidence available within its own repository.

Distributed search never centralizes humanitarian information.

---

# 9. Query Propagation

Implementations should avoid unlimited propagation of humanitarian Queries.

Typical propagation controls include:

- maximum hop count;
- time-to-live (TTL);
- trusted peer restrictions;
- geographic boundaries;
- organizational boundaries.

These mechanisms improve scalability while preserving decentralized operation.

Propagation policies remain implementation-specific.

---

# 10. Result Collection

Each participating HCP Node returns the Humanitarian Records matching the received Query.

Returned Humanitarian Records remain independent humanitarian observations.

Nodes never merge Humanitarian Records during search execution.

Every returned Humanitarian Record preserves its original humanitarian meaning.

Correlation begins only after the available humanitarian evidence has been collected.
---

# 11. Correlation After Search

Search concludes once the available Humanitarian Records have been collected.

From that point onward, the local HCP Node executes its Correlation Model.

Search never performs:

- humanitarian correlation;
- Humanitarian Timeline reconstruction;
- Humanitarian Case generation;
- result presentation.

These operations belong to subsequent protocol stages.

The Search and Query Protocol retrieves humanitarian evidence.

The Correlation Model interprets that evidence.

---

# 12. Query Completion

A humanitarian search may complete under different conditions.

Typical completion conditions include:

- all selected HCP Nodes have responded;
- the configured timeout has expired;
- the maximum search scope has been reached;
- local operational policies terminate the search.

Partial results remain valid humanitarian evidence.

Future synchronization or subsequent searches may reveal additional Humanitarian Records.

---

# 13. Fault Tolerance

Distributed humanitarian environments naturally experience communication failures.

Unavailable HCP Nodes should never prevent humanitarian search from completing.

Search continues using the Humanitarian Records successfully retrieved.

Temporary communication failures affect search completeness.

They do not affect protocol interoperability.

---

# 14. Privacy

Each HCP Node determines which Humanitarian Records are available for search according to its local policies.

Implementations may restrict searchable Humanitarian Records based on:

- organizational policies;
- local legislation;
- humanitarian context;
- access permissions.

Search never requires every Humanitarian Record to be publicly searchable.

Node autonomy remains one of the fundamental principles of HCP.

---

# 15. Security

Implementations should validate incoming Queries before executing humanitarian searches.

Typical validation includes:

- protocol compatibility;
- Query integrity;
- authorization policies;
- supported protocol version.

Invalid or malformed Queries should be rejected before search execution.

Security mechanisms remain implementation-specific.

---

# 16. Rate Limiting

Implementations are encouraged to protect humanitarian search services against abusive or excessive querying.

Typical mechanisms include:

- request quotas;
- authentication;
- query throttling;
- caching;
- trusted peer prioritization.

Rate limiting policies remain implementation-specific.

They should never alter the semantic behavior of humanitarian search.

---

# 17. Transport Independence

The Search and Query Protocol intentionally avoids prescribing communication technologies.

Compatible implementations may execute humanitarian searches using:

- HTTPS;
- gRPC;
- Message Queues;
- MQTT;
- WebSockets;
- offline synchronization;
- future communication mechanisms.

Regardless of the transport technology used, humanitarian search semantics remain identical.

---

# 18. Version Compatibility

HCP Nodes should advertise the protocol versions they support.

Search operations should use only features compatible with both communicating Nodes.

Whenever reasonably possible, backward compatibility should be preserved across protocol versions.

Version negotiation affects implementation compatibility.

It never changes humanitarian semantics.

---

# 19. Relationship with Other Specifications

The Search and Query Protocol defines how HCP Nodes execute humanitarian searches using standardized Queries.

Complementary specifications define the remaining stages of humanitarian interoperability.

- **HCP-0002** defines the HCP Node.
- **HCP-0005** defines the Node Communication Protocol.
- **HCP-0011** defines the Query Model.
- **HCP-0012** defines the Correlation Model.
- **HCP-0013** defines the Synchronization Model.
- **HCP-0015** defines the Result Presentation Model.

Together, these specifications define how humanitarian evidence is queried, retrieved, interpreted and ultimately presented while preserving decentralization and implementation independence.

---

# 20. Summary

The Search and Query Protocol defines the semantic principles governing humanitarian search within HCP.

Search retrieves Humanitarian Records.

It never retrieves identities.

The protocol intentionally separates humanitarian evidence retrieval from humanitarian interpretation.

Humanitarian understanding emerges only after correlation evaluates the available Humanitarian Records.

Different HCP Nodes may execute humanitarian searches using different implementation strategies while preserving identical semantic behavior.

By separating search, correlation and presentation into independent protocol stages, HCP maintains scalability, implementation independence and long-term interoperability.

The Search and Query Protocol reinforces one of the central architectural principles of HCP:

**Search retrieves humanitarian evidence.**

**Correlation creates humanitarian understanding.**

**Clients communicate Humanitarian Cases.**

**People verify reality.**
