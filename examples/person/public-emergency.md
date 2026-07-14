# Public Emergency

This example demonstrates how the Humanitarian Connection Protocol (HCP) represents the observation of a person requiring immediate public assistance.

Unlike a missing person or a hospitalized patient, this scenario records an emergency observation made in a public location.

The Humanitarian Record represents only what has been observed.

It does not establish identity.

It does not diagnose medical conditions.

It does not determine humanitarian outcomes.

---

# Humanitarian Scenario

A volunteer walking through a public square observes an elderly man sitting on the ground appearing confused and unable to respond coherently.

Emergency medical services have already been contacted.

The volunteer creates a Humanitarian Record using an HCP-compatible application so nearby humanitarian organizations and emergency responders may become aware of the observation.

At this moment:

- the volunteer does not know the person's identity;
- no hospital has confirmed admission;
- no family member has been identified;
- no humanitarian correlation has yet been performed.

Only one humanitarian observation exists.

---

# Humanitarian Observation

The volunteer observes:

- an elderly man;
- approximately 78 years old;
- unable to communicate clearly;
- sitting near the main entrance of the public square;
- wearing a gray sweater and black trousers.

These observations become one immutable Humanitarian Record.

---

# Expected Humanitarian Record

The corresponding Canonical JSON is provided in:

```text
public-emergency.json
```

This JSON represents one humanitarian observation describing a person requiring immediate public assistance.

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

        ├────────► Emergency Medical Services

        ├────────► Local Hospital

        └────────► Emergency Operations Center
```

Each participating HCP Node stores the Humanitarian Record independently.

The observation remains immutable throughout synchronization.

---

# Humanitarian Search

Later, another organization may perform a humanitarian search.

The Query may retrieve this Humanitarian Record together with other observations describing similar individuals.

Search retrieves humanitarian observations.

It never determines whether they describe the same person.

---

# Humanitarian Correlation

The local HCP Node evaluates every available Humanitarian Record.

Illustrative correlation factors include:

- compatible reported names (if available);
- similar estimated age;
- nearby observation locations;
- matching recognition features;
- compatible observation timestamps.

Correlation remains entirely local.

Different organizations may legitimately reach different humanitarian interpretations.

---

# Humanitarian Case

If sufficient compatible observations are identified, the local HCP Node may generate a Humanitarian Case describing the possible relationship between multiple Humanitarian Records.

Only Humanitarian Records participate in synchronization.

Humanitarian Cases remain local to each HCP Node.

---

# Human Verification

Emergency responders, healthcare professionals, volunteers and family members remain responsible for confirming the person's identity and determining the appropriate humanitarian response.

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

This example demonstrates that HCP also supports humanitarian observations involving immediate public emergencies.

The protocol does not synchronize medical diagnoses or humanitarian conclusions.

It synchronizes structured humanitarian observations describing situations that may require assistance.

Every participating HCP Node independently constructs humanitarian understanding from the available observations while preserving semantic interoperability.
