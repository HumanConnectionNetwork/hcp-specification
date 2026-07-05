# HCP-0014
# Query & Discovery Model

Version: 0.1 (Draft)

Status: Draft

Category: Core Specification

Authors: Human Connection Network Foundation

License: Apache-2.0

Last Updated: 2026-07-05

Depends On:

- HCP-0001 Humanitarian Record
- HCP-0002 HCP Node
- HCP-0005 Node Communication Protocol
- HCP-0006 Trust Model
- HCP-0012 Correlation Candidate
- HCP-0013 Synchronization Model

---

# 1. Abstract

The HCP Query & Discovery Model defines how humanitarian information is searched across HCP Nodes.

Unlike traditional databases, HCP does not search for people.

Instead, it searches for Humanitarian Records that are likely to describe the humanitarian situation being requested.

Search results represent observations ordered by probability rather than exact identity.

---

# 2. Purpose

The purpose of discovery is to assist humanitarian actors in locating relevant information during emergencies.

Typical examples include:

- locating missing persons
- checking hospital admissions
- finding evacuation records
- discovering shelter registrations
- locating rescue reports

The protocol assists human decision-making.

It does not attempt to identify individuals with certainty.

---

# 3. Search Philosophy

Traditional databases ask:

"Who is this person?"

HCP asks:

"Which observations most likely describe this humanitarian situation?"

This distinction allows multiple independent reports to coexist without forcing a single identity.

---

# 4. Search Input

A query may contain one or more search parameters.

Typical inputs include:

- reported name
- estimated age
- gender (optional)
- event type
- city
- region
- country
- date range
- reporting organization
- observation keywords

Partial information is expected.

---

# 5. Flexible Search

Queries should tolerate incomplete information.

Example:

Input:

Name:
Juan Perez

Age:
approximately 40

City:
Mérida

The system should not require exact matches.

Approximate matching is encouraged.

---

# 6. Local Discovery

Every query begins locally.

The node searches its own Humanitarian Records.

If sufficient information exists, results may be returned immediately.

---

# 7. Distributed Discovery

If configured, a node may expand the search.

```
Client

↓

Local Node

↓

Connected Peers

↓

Additional Nodes

↓

Aggregated Results

↓

Correlation

↓

Ranked Response
```

Each participating node performs the same search independently.

---

# 8. Result Collection

Every responding node returns matching Humanitarian Records.

No node returns a "person."

Each response contains independent observations.

---

# 9. Correlation

After records are collected, the Correlation Candidate algorithm is executed.

Its purpose is to identify observations that may describe the same humanitarian situation.

Correlation is probabilistic.

It never creates certainty.

---

# 10. Ranking

Search results should be ordered according to multiple factors.

Possible ranking signals include:

- Correlation Score
- Trust Score
- temporal proximity
- geographic proximity
- observation consistency
- number of independent observations

Higher confidence appears first.

---

# 11. Example

Query:

Name:
Maria Gonzalez

Age:
15

Location:
Valencia

Results:

Observation A

Hospital

Age 14

Valencia

Confidence: High

------------------------

Observation B

Volunteer

Age 15

Naguanagua

Confidence: Medium

------------------------

Observation C

Shelter

Age Unknown

Valencia

Confidence: Medium

The user evaluates the available information.

The protocol makes no final identification.

---

# 12. Query Expansion

Nodes may broaden searches automatically.

Examples include:

accent normalization

nickname matching

minor spelling variations

approximate age

neighboring locations

nearby dates

These techniques improve humanitarian discovery.

---

# 13. Privacy Considerations

Nodes remain free to restrict searchable fields.

Examples:

internal observations

protected organizations

restricted shelters

confidential medical facilities

Discovery policies remain under local node control.

---

# 14. Search Scope

Queries may target:

local node only

trusted nodes

specific organizations

regional networks

national networks

global HCP networks

The scope is determined by local policy.

---

# 15. Performance

Large humanitarian networks may contain millions of Humanitarian Records.

Nodes are encouraged to maintain local search indexes.

Synchronization and indexing are independent processes.

---

# 16. Failure Handling

If remote nodes are unavailable:

local results remain available.

Distributed search resumes whenever connectivity returns.

Emergency operation must never depend on a single node.

---

# 17. Human Interpretation

Search results are recommendations.

Final interpretation always belongs to human operators.

The protocol assists humanitarian work.

It never replaces human judgment.

---

# 18. Future Extensions

Future versions may include:

semantic search

multilingual search

phonetic matching

AI-assisted ranking

geographical clustering

federated search optimization

These extensions must remain compatible with existing HCP implementations.

---

# 19. Summary

The Query & Discovery Model enables decentralized humanitarian search across independent HCP Nodes.

Queries retrieve Humanitarian Records rather than identities.

Correlation Candidate estimates possible relationships.

Trust Model evaluates credibility.

Together these mechanisms provide a scalable and interoperable discovery system suitable for humanitarian emergencies without requiring centralized databases.
