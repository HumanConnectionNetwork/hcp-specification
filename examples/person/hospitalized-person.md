# Hospitalized Person

This example demonstrates how a healthcare organization records the admission of an unidentified or partially identified patient using the Humanitarian Connection Protocol (HCP).

The purpose of this example is to illustrate how hospitals contribute humanitarian observations without attempting to determine whether the patient corresponds to reports created by other organizations.

---

# Humanitarian Scenario

Following a large earthquake, emergency responders transport an elderly woman to a regional hospital.

The patient is conscious but unable to provide complete identification.

Hospital staff create a Humanitarian Record describing the patient as observed during admission.

At this moment:

- the hospital does not know whether the patient has been reported missing;
- no family member has been identified;
- no humanitarian correlation has yet been performed.

Only one humanitarian observation exists.

---

# Humanitarian Observation

Hospital staff observe:

- an elderly woman;
- approximately 74 years old;
- responding to the name "María";
- admitted through the emergency department;
- wearing a blue jacket and carrying a small black backpack.

These observations become a single immutable Humanitarian Record.

---

# Expected Humanitarian Record

The corresponding Canonical JSON is provided in:

```text
hospitalized-person.json
```

This JSON represents one humanitarian observation made during hospital admission.

It does not confirm the patient's identity.

---

# Synchronization

After admission, the Humanitarian Record may be synchronized with other participating HCP Nodes.

Illustrative example:

```text
Hospital Information System

        │

        ▼

Hospital HCP Node

        │

──────── Synchronization ────────

        │

        ├────────► Emergency Operations Center

        ├────────► Humanitarian Organization

        └────────► Regional Federation
```

Each receiving HCP Node stores the Humanitarian Record independently.

The observation remains immutable throughout synchronization.

---

# Humanitarian Search

Hours later, a family searching for a missing relative submits a humanitarian Query.

The local HCP Node retrieves multiple Humanitarian Records, including this hospital admission.

Search retrieves humanitarian observations.

It does not determine whether they describe the same individual.

---

# Humanitarian Correlation

The local HCP Node evaluates all available Humanitarian Records.

Illustrative correlation factors include:

- compatible reported names;
- similar estimated age;
- nearby observation locations;
- matching recognition features;
- compatible observation timestamps.

Each HCP Node performs this evaluation independently.

No humanitarian interpretation is synchronized.

---

# Humanitarian Case

If sufficient compatible observations are identified, the local HCP Node may construct a Humanitarian Case.

The Humanitarian Case summarizes the available humanitarian evidence supporting the possible relationship between the hospital admission and other observations.

Only Humanitarian Records participate in synchronization.

Humanitarian Cases always remain local.

---

# Human Verification

Hospital staff, family members and emergency responders remain responsible for confirming whether the admitted patient is actually the missing person.

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

This example demonstrates another fundamental architectural principle of HCP.

Hospitals do not synchronize identified patients.

They synchronize humanitarian observations describing hospital admissions.

Every participating HCP Node independently evaluates those observations together with other available humanitarian evidence to construct its own humanitarian understanding.
