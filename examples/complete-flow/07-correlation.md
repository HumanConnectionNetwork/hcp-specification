# Correlation

This example demonstrates how an HCP Node performs local correlation after retrieving multiple Humanitarian Records.

The purpose of correlation is to evaluate whether independent humanitarian observations may describe the same humanitarian situation.

Correlation never modifies Humanitarian Records.

Instead, it analyzes the available evidence and constructs a local humanitarian interpretation.

---

# Starting Point

The previous search operation returned four Humanitarian Records.

Each record was created independently by a different organization.

None of the organizations attempted to determine identity.

At this stage, the HCP Node possesses only humanitarian observations.

```text
Search

        │

        ▼

4 Humanitarian Records
```

The next step is local correlation.

---

# Humanitarian Evidence

The HCP Node evaluates every available Humanitarian Record.

Illustrative observations include:

| Event Type | Organization |
|------------|--------------|
| Missing Person | Family |
| Hospitalized Person | Hospital |
| Refugee Person | Shelter |
| Found Person | Volunteer |

Each observation contributes independent humanitarian evidence.

None of them proves identity.

---

# Supporting Evidence

The HCP Node identifies several compatible observations.

Illustrative Supporting Evidence includes:

- reported labels are compatible ("María González" and "María");
- estimated ages are identical;
- recognition features are highly consistent;
- reported locations follow a plausible evacuation path;
- observation timestamps describe a realistic humanitarian sequence.

Individually, none of these observations is conclusive.

Together, they strengthen the humanitarian hypothesis.

---

# Conflicting Evidence

Correlation also evaluates observations that may weaken the hypothesis.

Illustrative examples include:

- incomplete reported labels;
- minor differences in reported locations;
- missing information in some observations.

In this example, no significant conflicts prevent correlation.

Instead, the HCP Node records these differences as part of the humanitarian reasoning.

---

# Humanitarian Reasoning

Based on the available observations, the HCP Node constructs an explanation describing why the records appear related.

Illustrative reasoning includes:

- all observations describe an elderly woman;
- estimated ages are compatible;
- physical characteristics remain consistent;
- reported locations are geographically plausible;
- timestamps follow a realistic chronological sequence.

This reasoning increases transparency.

It does not establish identity.

---

# Humanitarian Case

After evaluating all available evidence, the HCP Node generates a Humanitarian Case.

The Humanitarian Case summarizes the humanitarian interpretation produced by the local Correlation Model.

The Humanitarian Case includes:

- related Humanitarian Records;
- supporting evidence;
- conflicting evidence;
- humanitarian reasoning;
- local confidence assessment.

Unlike Humanitarian Records, the Humanitarian Case is never synchronized.

---

# Human Verification

The Humanitarian Case assists humanitarian coordination.

Final verification remains the responsibility of people.

Family members, volunteers, hospitals and humanitarian organizations determine whether the observations actually describe the same person.

Technology organizes evidence.

People confirm reality.

---

# End of the Flow

At the conclusion of correlation, the HCP Node has transformed independent humanitarian observations into a structured humanitarian interpretation.

```text
Humanitarian Records

        │

        ▼

Correlation

        │

        ▼

Supporting Evidence

        │

        ▼

Conflicting Evidence

        │

        ▼

Humanitarian Reasoning

        │

        ▼

Humanitarian Case
```

Only the Humanitarian Records participate in interoperability.

The Humanitarian Case remains local.

---

# Related Specifications

This example illustrates concepts defined by:

- HCP-0012 — Correlation Model
- HCP-0014 — Explainable Correlation Model
- HCP-0015 — Result Presentation Model

---

# Summary

This example demonstrates how HCP Nodes independently transform humanitarian observations into humanitarian understanding.

Observations remain immutable.

Interpretation remains local.

Human verification remains essential.

HCP synchronizes observations.

It never synchronizes conclusions.
