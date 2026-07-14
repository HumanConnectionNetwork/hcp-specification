# Found Person

This example demonstrates how a volunteer, emergency responder or humanitarian organization records the observation of a person who has been found during a humanitarian emergency using the Humanitarian Connection Protocol (HCP).

The purpose of this example is to illustrate how HCP records humanitarian observations describing a person who has been located without assuming identity or humanitarian outcome.

The Humanitarian Record represents only what was observed.

It does not confirm who the person is.

---

# Humanitarian Scenario

Several hours after severe flooding, a volunteer team discovers an elderly woman walking safely near an evacuation route.

The woman appears disoriented and cannot provide complete personal information.

A volunteer creates a Humanitarian Record describing the observation using an HCP-compatible application.

At this moment:

- the volunteer does not know whether the person has been reported missing;
- no family member has confirmed her identity;
- no humanitarian correlation has yet been performed.

Only one humanitarian observation exists.

---

# Humanitarian Observation

The volunteer observes:

- an elderly woman;
- approximately 74 years old;
- responding to the name "María";
- located near an evacuation route;
- wearing a blue jacket and carrying a small black backpack.

These observations become a single immutable Humanitarian Record.

---

# Expected Humanitarian Record

The corresponding Canonical JSON is provided in:

```text
found-person.json
```

This JSON represents one humanitarian observation describing a person who has been located.

It does not establish identity.

---

# Synchronization

After creation, the Humanitarian Record may be synchronized with other participating HCP Nodes.

Illustrative example:

```text
Volunteer Mobile Client

        │

        ▼

Volunteer HCP Node

        │

──────── Synchronization ────────

        │

        ├────────► Hospital

        ├────────► Shelter

        └────────► Emergency Operations Center
```

Each participating HCP Node stores the Humanitarian Record independently.

The observation remains immutable throughout synchronization.

---

# Humanitarian Search

Later, another organization may perform a humanitarian search.

The Query may retrieve this Humanitarian Record together with observations describing:

- a missing person;
- a hospitalized person;
- a sheltered person.

Search retrieves humanitarian observations.

It never determines whether they describe the same individual.

---

# Humanitarian Correlation

The local HCP Node evaluates every available Humanitarian Record.

Illustrative correlation factors include:

- compatible reported names;
- similar estimated age;
- nearby observation locations;
- matching recognition features;
- compatible observation timestamps.

Each HCP Node performs correlation independently.

No humanitarian interpretation is exchanged.

---

# Humanitarian Case

If sufficient compatible observations are available, the local HCP Node may generate a Humanitarian Case relating this observation to previously reported humanitarian observations.

Only Humanitarian Records participate in synchronization.

Humanitarian Cases remain local.

---

# Human Verification

Volunteers, emergency responders, family members and humanitarian organizations remain responsible for confirming whether the located person corresponds to previously reported observations.

HCP assists humanitarian coordination.

It never replaces direct human verification.

---

# Related Specifications

This example illustrates concepts defined by:

- HCP-0001 — Humanitarian Record
- HCP-0010 — Canonical JSON Specification
- HCP-0012 — Correlation Model
- HCP-0014 — Explainable Correlation Model
- HCP-0015 — Result Presentation Model
- HCP-0018 — Search Protocol

---

# Summary

This example demonstrates how HCP records the observation of a person who has been located without attempting to determine identity or synchronize humanitarian conclusions.

Every Humanitarian Record represents one immutable observation.

Humanitarian understanding emerges later through local correlation of multiple independent observations originating from families, hospitals, shelters, volunteers and other participating organizations.
