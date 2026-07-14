# Refugee Person

This example demonstrates how a shelter or humanitarian organization records the arrival of a displaced person using the Humanitarian Connection Protocol (HCP).

The purpose of this example is to illustrate how humanitarian organizations contribute structured observations describing people who have sought temporary refuge during a humanitarian emergency.

The Humanitarian Record represents the observation made by the receiving organization.

It does not determine the person's complete identity or humanitarian history.

---

# Humanitarian Scenario

Following widespread flooding, a temporary community shelter receives an elderly woman seeking assistance.

The woman explains that she became separated from relatives during the evacuation.

Shelter volunteers register the observation using an HCP-compatible application.

At this moment:

- the shelter does not know whether the person has been reported missing;
- no hospital has reported admitting the person;
- no humanitarian correlation has yet been performed.

Only one humanitarian observation exists.

---

# Humanitarian Observation

Shelter staff observe:

- an elderly woman;
- approximately 74 years old;
- responding to the name "María";
- recently arrived at the community shelter;
- wearing a blue jacket and carrying a small black backpack.

These observations become a single immutable Humanitarian Record.

---

# Expected Humanitarian Record

The corresponding Canonical JSON is provided in:

```text
refugee-person.json
```

This JSON represents one humanitarian observation describing a person temporarily sheltered.

It does not establish identity.

---

# Synchronization

After registration, the Humanitarian Record may be synchronized with other participating HCP Nodes.

Illustrative example:

```text
Shelter Management System

        │

        ▼

Shelter HCP Node

        │

──────── Synchronization ────────

        │

        ├────────► Emergency Operations Center

        ├────────► Humanitarian Organization

        └────────► Regional Hospital
```

Each participating HCP Node stores the observation independently.

The Humanitarian Record remains immutable.

---

# Humanitarian Search

Later, a humanitarian search may retrieve this Humanitarian Record together with observations originating from hospitals, volunteers or family members.

Search retrieves humanitarian observations.

It never determines whether those observations describe the same person.

---

# Humanitarian Correlation

The local HCP Node evaluates all available Humanitarian Records.

Illustrative correlation factors include:

- compatible reported names;
- similar estimated age;
- nearby reported locations;
- matching recognition features;
- compatible observation timestamps.

Correlation produces humanitarian interpretations locally.

No interpretation is exchanged between organizations.

---

# Humanitarian Case

If sufficient humanitarian evidence is available, the local HCP Node may generate a Humanitarian Case relating this shelter observation to other compatible Humanitarian Records.

Only Humanitarian Records participate in synchronization.

Humanitarian Cases remain local to each HCP Node.

---

# Human Verification

Shelter personnel, family members, emergency responders and humanitarian organizations remain responsible for confirming whether the sheltered person corresponds to reports created elsewhere.

HCP supports humanitarian coordination.

It never replaces human verification.

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

This example demonstrates how shelters and humanitarian organizations contribute humanitarian observations describing displaced people without attempting to establish identity or synchronize humanitarian conclusions.

Each Humanitarian Record represents one observation.

Humanitarian understanding emerges later through local correlation of multiple independent observations.
