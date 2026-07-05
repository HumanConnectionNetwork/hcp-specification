# HCP-0018
# Search & Query Protocol

Version: 0.1 (Draft)

Status: Draft

Category: Core Specification

Authors: Human Connection Network Foundation

License: Apache-2.0

Last Updated: 2026-07-05

Depends On:

- HCP-0002 HCP Node
- HCP-0005 Node Communication Protocol
- HCP-0006 Trust Model
- HCP-0012 Correlation Candidate
- HCP-0013 Synchronization Model
- HCP-0014 Query & Discovery Model
- HCP-0017 Event Classification Model

---

# 1. Abstract

The Search & Query Protocol defines how HCP Nodes request and exchange humanitarian observations.

The protocol specifies query behavior rather than transport mechanisms.

An HCP query searches for Humanitarian Records that may describe a requested humanitarian situation.

It never requests or returns verified personal identities.

---

# 2. Purpose

Search allows independent HCP Nodes to discover humanitarian observations stored by other participating nodes.

The objective is to improve humanitarian awareness while preserving decentralization and interoperability.

---

# 3. Design Principles

Search operations shall be:

- decentralized
- transport independent
- stateless
- deterministic
- interoperable
- fault tolerant

Nodes remain autonomous.

No central search authority exists.

---

# 4. Query Model

A query represents a humanitarian search request.

Typical search parameters may include:

- reported name
- estimated age
- estimated gender
- event classification
- city
- administrative region
- country
- date range
- reporting organization
- free text keywords

All parameters are optional.

Partial searches are expected.

---

# 5. Query Scope

Nodes may execute searches against:

- local records
- selected trusted peers
- regional HCP networks
- national HCP networks
- global HCP networks

Scope is determined by local policy.

---

# 6. Local Search

Every search begins locally.

If local observations satisfy the request, results may be returned immediately.

Remote searches remain optional.

---

# 7. Distributed Search

When enabled, the node may forward the query to connected peers.

Example:

```
Client

↓

Node A

↓

Node B

↓

Node C

↓

Node D
```

Each node performs an independent search.

---

# 8. Query Propagation

Nodes should avoid unlimited query propagation.

Typical mechanisms include:

- maximum hop count
- time-to-live (TTL)
- trusted peer restrictions
- geographic limits

These mechanisms reduce unnecessary network traffic.

---

# 9. Query Parameters

Queries should tolerate incomplete or uncertain information.

Example:

```
Reported Name:
Maria González

Estimated Age:
15

Location:
Valencia

Event:
Hospital Admission
```

Exact matches are not required.

---

# 10. Result Collection

Each node returns matching Humanitarian Records.

Returned records remain independent observations.

Nodes must not merge records during query execution.

---

# 11. Correlation

Correlation is performed after records are collected.

The Correlation Candidate algorithm estimates whether multiple observations describe the same humanitarian situation.

Correlation never modifies returned records.

---

# 12. Ranking

Returned observations should be ranked using:

- Correlation Score
- Trust Score
- temporal proximity
- geographic proximity
- observation consistency
- event similarity

Ranking assists human interpretation.

---

# 13. Query Completion

A query completes when:

- all configured nodes respond;
- timeout expires;
- maximum search scope is reached;
- local policy terminates the operation.

Partial results remain valid.

---

# 14. Fault Tolerance

Unavailable nodes must not prevent search execution.

The querying node continues using available observations.

Future synchronization may reveal additional information.

---

# 15. Privacy

Nodes remain responsible for determining which observations may be searchable.

Private records need not participate in distributed search.

Local policy always prevails.

---

# 16. Security

Nodes should verify:

- requesting node identity (when applicable)
- protocol compatibility
- query integrity
- authorization policies

Invalid queries should be rejected.

---

# 17. Rate Limiting

Implementations are encouraged to protect against abusive querying.

Possible mechanisms include:

- request quotas
- authentication
- query throttling
- caching
- trusted-node prioritization

Rate limiting is implementation specific.

---

# 18. Transport Independence

The Search & Query Protocol does not mandate a transport technology.

Implementations may use:

- HTTPS
- gRPC
- Message Queues
- MQTT
- WebSockets
- Offline synchronization
- Future communication mechanisms

Semantic behavior must remain consistent.

---

# 19. Version Compatibility

Nodes should advertise supported protocol versions.

Queries should only use features supported by both parties.

Backward compatibility is strongly recommended.

---

# 20. Future Extensions

Future versions may support:

- semantic search
- multilingual search
- phonetic search
- AI-assisted query expansion
- geographic indexing
- distributed caching
- encrypted federated search

Extensions should preserve interoperability whenever possible.

---

# 21. Summary

The Search & Query Protocol enables decentralized discovery of humanitarian observations across independent HCP Nodes.

Queries retrieve observations rather than identities.

Correlation and Trust Models organize the returned information.

This approach allows scalable humanitarian search while preserving decentralization, interoperability and local autonomy.
