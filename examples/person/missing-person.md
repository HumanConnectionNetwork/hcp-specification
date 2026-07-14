# Missing Person

This example demonstrates one of the most common humanitarian situations supported by the Humanitarian Connection Protocol (HCP).

A family member reports a missing person after losing contact during a humanitarian emergency.

The purpose of this example is to illustrate how a Humanitarian Record represents a single humanitarian observation without attempting to determine identity or humanitarian outcome.

---

# Humanitarian Scenario

Following severe flooding, a family can no longer locate an elderly relative.

The relative was last seen leaving a temporary shelter several hours earlier.

A family member submits a humanitarian observation using an HCP-compatible client.

The application creates a new Humanitarian Record describing that observation.

At this moment:

- the person's actual location is unknown;
- no hospital has confirmed admission;
- no rescue team has reported contact;
- no humanitarian correlation has yet been performed.

Only one humanitarian observation exists.

---

# Humanitarian Observation

The reporting person observed:

- an elderly woman;
- approximately 74 years old;
- known locally as "María González";
- last seen near the Central Community Shelter;
- wearing a blue jacket and carrying a small black backpack.

These observations become a single immutable Humanitarian Record.

---

# Expected Humanitarian Record

The corresponding Canonical JSON is provided in:

```text
missing-person.json
```

This JSON represents exactly one humanitarian observation.

It does not represent a confirmed identity.

---

# Synchronization

After creation, the Humanitarian Record may be synchronized with other compatible HCP Nodes.

Illustrative example:

```text
Family Client

        │

        ▼

Local HCP Node

        │

──────── Synchronization ────────

        │

        ├────────► Hospital

        ├────────► Shelter

        └────────► Emergency Operations Center
```

Each participating HCP Node stores the Humanitarian Record independently.

The Humanitarian Record remains unchanged throughout synchronization.

---

# Humanitarian Search

Later, another organization may perform a humanitarian search.

The Query may retrieve this Humanitarian Record together with additional observations describing similar individuals.

Search retrieves humanitarian observations.

It does not determine whether those observations describe the same person.

---

# Humanitarian Correlation

After search completes, the local HCP Node evaluates the available Humanitarian Records.

Possible correlation factors include:

- similar reported names;
- compatible estimated ages;
- nearby reported locations;
- compatible observation times;
- matching recognition features.

Correlation remains entirely local.

Different organizations may legitimately produce different humanitarian interpretations.

---

# Humanitarian Case

If multiple compatible Humanitarian Records are identified, the local HCP Node may generate a Humanitarian Case.

The Humanitarian Case summarizes the available humanitarian evidence.

It is never synchronized with other HCP Nodes.

Only the original Humanitarian Records participate in synchronization.

---

# Human Verification

A Humanitarian Case assists humanitarian decision making.

It never replaces direct verification.

Family members, hospitals, emergency responders or humanitarian organizations remain responsible for confirming whether the observations actually describe the missing person.

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

This example demonstrates one of the fundamental architectural principles of HCP.

The protocol does not synchronize missing persons.

It synchronizes humanitarian observations describing missing persons.

Every participating HCP Node independently constructs humanitarian understanding from the available observations while preserving semantic interoperability.
