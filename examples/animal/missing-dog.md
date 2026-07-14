# Missing Dog

This example demonstrates how the Humanitarian Connection Protocol (HCP) represents the observation of a missing dog.

Although this example involves an animal rather than a person, exactly the same architectural principles apply.

The Humanitarian Record represents one humanitarian observation.

It does not establish ownership.

It does not determine the animal's current location.

It does not synchronize humanitarian conclusions.

---

# Humanitarian Scenario

Following a severe storm, a family can no longer locate their dog after evacuating their neighborhood.

The dog disappeared during the evacuation and has not returned.

A family member creates a Humanitarian Record using an HCP-compatible application.

At this moment:

- the dog's current location is unknown;
- no volunteer has reported finding the animal;
- no shelter has registered the animal;
- no humanitarian correlation has yet been performed.

Only one humanitarian observation exists.

---

# Humanitarian Observation

The reporting person observes:

- a medium-sized dog;
- known by the name "Max";
- mixed breed;
- light brown coat;
- wearing a red collar;
- last seen near Riverside Park during the evacuation.

These observations become one immutable Humanitarian Record.

---

# Expected Humanitarian Record

The corresponding Canonical JSON is provided in:

```text
missing-dog.json
```

This JSON represents one humanitarian observation describing a missing animal.

It does not establish ownership.

---

# Synchronization

After creation, the Humanitarian Record may be synchronized with other participating HCP Nodes.

Illustrative example:

```text
Family Client

        │

        ▼

Local HCP Node

        │

──────── Synchronization ────────

        │

        ├────────► Animal Shelter

        ├────────► Volunteer Network

        └────────► Municipal Emergency Center
```

Each participating HCP Node stores the Humanitarian Record independently.

The observation remains immutable throughout synchronization.

---

# Humanitarian Search

Later, another organization may perform a humanitarian search.

The Query may retrieve this Humanitarian Record together with additional observations describing similar animals.

Search retrieves humanitarian observations.

It never determines whether they describe the same animal.

---

# Humanitarian Correlation

The local HCP Node evaluates every available Humanitarian Record.

Illustrative correlation factors include:

- compatible reported name;
- compatible species;
- similar size;
- similar breed;
- matching recognition features;
- nearby reported locations;
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

Animal shelters, volunteers and the reporting family remain responsible for confirming whether the located animal is actually the missing dog.

HCP assists humanitarian coordination.

It never replaces direct verification.

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

This example demonstrates that HCP applies the same architectural principles to animals as it does to people.

The protocol does not synchronize missing animals.

It synchronizes humanitarian observations describing missing animals.

Every participating HCP Node independently constructs humanitarian understanding from the available observations while preserving semantic interoperability.
