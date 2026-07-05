# HCP-0022
# Interoperability Requirements

Version: 0.1 (Draft)

Status: Draft

Category: Core Specification

Authors: Human Connection Network Foundation

License: Apache-2.0

Last Updated: 2026-07-05

Depends On:

- HCP-0001 Humanitarian Record
- HCP-0002 HCP Node
- HCP-0004 Node Identity
- HCP-0005 Node Communication Protocol
- HCP-0006 Trust Model
- HCP-0012 Correlation Candidate
- HCP-0013 Synchronization Model
- HCP-0014 Query & Discovery Model
- HCP-0017 Event Classification Model
- HCP-0018 Search & Query Protocol
- HCP-0019 Federation & Node Discovery Model
- HCP-0020 Security Model
- HCP-0021 Privacy & Data Minimization

---

# 1. Abstract

This specification defines the minimum technical requirements for an implementation to claim interoperability with the Humanitarian Connection Protocol (HCP).

These requirements establish consistent behavior across independent implementations while preserving implementation flexibility.

---

# 2. Normative Language

The key words:

- MUST
- MUST NOT
- REQUIRED
- SHALL
- SHALL NOT
- SHOULD
- SHOULD NOT
- RECOMMENDED
- MAY
- OPTIONAL

are to be interpreted as described in RFC 2119 and RFC 8174.

---

# 3. General Requirements

An HCP implementation MUST exchange Humanitarian Records according to the protocol specifications.

An implementation MAY provide additional functionality provided that it does not break protocol interoperability.

Local implementation details remain outside the scope of HCP.

---

# 4. Humanitarian Records

An implementation MUST:

- generate valid Humanitarian Records;
- preserve immutable records;
- assign globally unique Record UUIDs;
- preserve timestamps;
- preserve metadata;
- preserve unknown optional fields.

An implementation MUST NOT modify synchronized records.

---

# 5. Record Immutability

Once a Humanitarian Record has been published, it MUST remain immutable.

New information MUST generate a new Humanitarian Record.

Existing records MUST NOT be edited.

---

# 6. Event Classification

Implementations MUST recognize standardized HCP Event Classifications.

Unknown Event Types MUST NOT invalidate otherwise valid records.

Implementations SHOULD preserve unknown classifications whenever possible.

---

# 7. Synchronization

Implementations MUST support synchronization of Humanitarian Records.

Synchronization MUST preserve:

- Record UUID;
- timestamps;
- metadata;
- event classification;
- signatures (when present).

Synchronization MUST NOT alter record content.

---

# 8. Query Support

Implementations SHOULD support distributed humanitarian queries.

Queries MUST return Humanitarian Records rather than identified persons.

Implementations MAY limit search scope according to local policy.

---

# 9. Correlation

Implementations SHOULD support Correlation Candidate processing.

Correlation MUST NOT merge Humanitarian Records.

Correlation MUST preserve original observations.

---

# 10. Trust Model

Trust evaluation SHOULD follow the principles defined in the HCP Trust Model.

Implementations MAY implement additional trust algorithms.

Trust evaluation MUST remain independent from cryptographic authentication.

---

# 11. Node Identity

Nodes participating in federated synchronization SHOULD possess stable identities.

Identity technologies remain implementation specific.

Node Identity MUST NOT alter Humanitarian Record semantics.

---

# 12. Security

Implementations SHOULD verify:

- record integrity;
- digital signatures (when available);
- protocol compatibility;
- federation policies.

Invalid records MUST be rejected.

---

# 13. Privacy

Implementations SHOULD exchange only the minimum information necessary for humanitarian coordination.

Privacy policies remain locally governed.

Implementations MUST NOT assume that all locally stored observations are eligible for synchronization.

---

# 14. Transport Independence

Implementations MAY use any communication technology.

Examples include:

- HTTPS
- gRPC
- MQTT
- Message Queues
- WebSockets
- Offline synchronization

Transport selection MUST NOT alter protocol semantics.

---

# 15. Federation

Implementations MAY participate in:

- private federations;
- public federations;
- hybrid federations.

Federation membership remains outside the scope of HCP.

---

# 16. Unknown Extensions

Implementations MUST ignore unknown optional fields without rejecting valid Humanitarian Records.

Unknown extensions SHOULD be preserved whenever technically possible.

This requirement improves forward compatibility.

---

# 17. Version Compatibility

Implementations SHOULD advertise supported HCP versions.

Nodes SHOULD negotiate compatible protocol behavior whenever multiple versions are available.

Backward compatibility is strongly recommended.

---

# 18. Error Handling

Implementations SHOULD detect and report:

- malformed records;
- invalid signatures;
- unsupported protocol versions;
- synchronization failures;
- invalid metadata.

Errors SHOULD NOT interrupt unrelated protocol operations.

---

# 19. Local Autonomy

HCP implementations remain free to define:

- governance;
- authentication policies;
- synchronization policies;
- retention policies;
- federation rules;
- operational procedures.

These local decisions MUST NOT modify the protocol semantics.

---

# 20. Compliance Levels

An implementation may describe itself as:

### HCP Compatible

Implements all mandatory (MUST) requirements.

---

### HCP Recommended

Implements mandatory and recommended (SHOULD) requirements.

---

### HCP Extended

Implements HCP plus additional vendor-specific capabilities without breaking interoperability.

Vendor-specific extensions SHOULD be documented.

---

# 21. Non-Compliance

An implementation MUST NOT claim HCP compatibility if it:

- modifies synchronized records;
- replaces immutable observations;
- alters standardized semantics;
- breaks protocol interoperability;
- violates mandatory requirements defined by this specification.

---

# 22. Future Compatibility

Future HCP versions should preserve interoperability whenever reasonably possible.

Breaking changes SHOULD be avoided.

When unavoidable, version negotiation mechanisms SHOULD be provided.

---

# 23. Summary

This specification defines the minimum technical requirements necessary for interoperable HCP implementations.

By distinguishing mandatory, recommended and optional behaviors, HCP enables diverse software implementations while preserving a consistent humanitarian interoperability model across organizations, technologies and deployment environments.
