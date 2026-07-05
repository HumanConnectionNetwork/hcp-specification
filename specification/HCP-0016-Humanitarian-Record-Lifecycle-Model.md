# HCP-0016
# Humanitarian Record Lifecycle Model

Version: 0.1 (Draft)

Status: Draft

Category: Core Specification

Authors: Human Connection Network Foundation

License: Apache-2.0

Last Updated: 2026-07-05

Depends On:

- HCP-0001 Humanitarian Record
- HCP-0005 Node Communication Protocol
- HCP-0006 Trust Model
- HCP-0012 Correlation Candidate
- HCP-0013 Synchronization Model
- HCP-0014 Query & Discovery Model

---

# 1. Abstract

The Humanitarian Record Lifecycle Model defines how humanitarian observations evolve over time within the Humanitarian Connection Protocol (HCP).

HCP does not modify previously published Humanitarian Records.

Instead, new observations are created whenever new humanitarian information becomes available.

The humanitarian history is therefore represented as a sequence of immutable observations.

---

# 2. Design Principle

Humanitarian Records are immutable.

Once published, a record must never be modified or replaced.

If new information becomes available, a new Humanitarian Record is created.

The protocol preserves the complete history of humanitarian observations.

---

# 3. Observation Lifecycle

Each Humanitarian Record follows a simple lifecycle.

```
Observation Created

↓

Validated by Node

↓

Stored Locally

↓

Synchronized

↓

Queried

↓

Correlated

↓

Presented to Users

↓

Remains Available as Historical Evidence
```

The record itself never changes.

---

# 4. Humanitarian Situation Evolution

A humanitarian situation evolves through new observations rather than updates.

Example:

Observation 1

Status:
Missing

↓

Observation 2

Status:
Located

↓

Observation 3

Status:
Hospitalized

↓

Observation 4

Status:
Discharged

Each observation is an independent Humanitarian Record.

---

# 5. Status Representation

Status values describe the humanitarian situation observed at the time of reporting.

Typical examples include:

- Missing
- Located
- Rescued
- Hospitalized
- Evacuated
- Sheltered
- Injured
- Deceased
- Safe
- Case Closed

These values represent observations, not permanent personal attributes.

---

# 6. No Record Updates

The following operation is prohibited:

```
Record A

Status:
Missing

↓

Update

↓

Status:
Hospitalized
```

Instead:

```
Record A

Status:
Missing

+

Record B

Status:
Hospitalized
```

Historical integrity is preserved.

---

# 7. Observation Timeline

Related observations may be presented chronologically.

Example:

08:15

Reported Missing

↓

10:40

Located

↓

11:30

Hospital Admission

↓

18:20

Discharged

The timeline is reconstructed during query.

It is never stored as a single object.

---

# 8. Correlation

The protocol does not define a lifecycle for individuals.

Correlation Candidate estimates whether independent observations are likely to describe the same humanitarian situation.

Correlation does not merge records.

---

# 9. Conflicting Observations

Different observations may report different statuses.

Example:

Observation A

Missing

Observation B

Hospitalized

Observation C

Evacuated

All observations remain valid historical evidence.

The protocol does not delete conflicting information.

---

# 10. Historical Preservation

Every Humanitarian Record remains available unless removed according to local retention policies.

Historical observations improve:

- transparency
- auditing
- traceability
- humanitarian analysis

---

# 11. Record Retirement

Nodes may archive older records according to local policy.

Archived records remain valid Humanitarian Records.

Archiving does not alter record content.

---

# 12. Case Closure

Case Closed is itself an observation.

It does not remove previous observations.

It simply indicates that, according to the reporting node, the humanitarian situation has concluded.

Other nodes remain free to publish additional observations if new information becomes available.

---

# 13. Synchronization

Every new observation is synchronized independently.

Nodes exchange records, not case histories.

Humanitarian history emerges through correlation.

---

# 14. Search Behavior

Queries reconstruct humanitarian history dynamically.

The protocol does not maintain a continuously updated case object.

Every search is built from available observations.

---

# 15. Privacy

Lifecycle reconstruction depends only on observations intentionally shared by participating nodes.

Organizations remain responsible for deciding which observations are published through HCP.

Internal operational records remain outside the scope of the protocol.

---

# 16. Future Extensions

Future versions may define:

- observation expiration policies
- disaster lifecycle classifications
- event grouping strategies
- automated timeline generation
- advanced historical analytics

These extensions must preserve record immutability.

---

# 17. Summary

The Humanitarian Record Lifecycle Model defines how humanitarian information evolves within HCP.

Records are immutable.

New information generates new observations.

Humanitarian history is reconstructed dynamically through correlated observations rather than stored as a continuously updated personal record.

This approach preserves transparency, traceability and interoperability while maintaining the protocol's focus on humanitarian events rather than individual identities.
