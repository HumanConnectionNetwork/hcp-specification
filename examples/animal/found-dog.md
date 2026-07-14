# Found Dog

This example demonstrates how the Humanitarian Connection Protocol (HCP) represents the observation of a dog that has been found during a humanitarian emergency.

The Humanitarian Record represents one humanitarian observation describing an animal that has been located.

It does not establish ownership.

It does not determine whether the animal corresponds to a previously reported missing dog.

Only humanitarian observations are synchronized.

---

# Humanitarian Scenario

Several hours after severe flooding, a volunteer discovers a medium-sized dog wandering near an emergency shelter.

The dog appears healthy but is wearing a red collar and shows signs of having been separated from its owner.

The volunteer creates a Humanitarian Record using an HCP-compatible application.

At this moment:

- the volunteer does not know whether the dog has been reported missing;
- no shelter has registered the animal;
- no humanitarian correlation has yet been performed.

Only one humanitarian observation exists.

---

# Humanitarian Observation

The volunteer observes:

- a medium-sized dog;
- responding to the name "Max";
- mixed breed;
- light brown coat;
- wearing a red collar;
- found near the Riverside Emergency Shelter.

These observations become one immutable Humanitarian Record.

---

# Expected Humanitarian Record

The corresponding Canonical JSON is provided in:

```text
found-dog.json
```

This JSON represents one humanitarian observation describing a found animal.

It does not establish ownership.

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

        ├────────► Animal Shelter

        ├────────► Municipal Animal Rescue

        └────────► Community Volunteer Network
```

Each participating HCP Node stores the Humanitarian Record independently.

The observation remains immutable throughout synchronization.

---

# Humanitarian Search

Later, another organization may perform a humanitarian search.

The Query may retrieve this Humanitarian Record together with observations describing missing animals.

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

Animal shelters, volunteers and the reporting family remain responsible for confirming whether the located animal actually corresponds to previously reported observations.

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

This example demonstrates how HCP records the observation of a found animal without attempting to determine ownership or synchronize humanitarian conclusions.

Every Humanitarian Record represents one immutable observation.

Humanitarian understanding emerges later through local correlation of multiple independent observations originating from families, volunteers, shelters and other participating organizations.
