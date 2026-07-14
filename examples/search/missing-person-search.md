# Missing Person Search

This example demonstrates how an HCP-compatible implementation performs a humanitarian search for a missing person.

The objective of the search is to retrieve Humanitarian Records that may be relevant to the humanitarian situation.

The search process does not determine identity.

It does not establish humanitarian conclusions.

It only retrieves humanitarian observations.

---

# Humanitarian Scenario

Several hours after a severe flood, a family continues searching for an elderly relative.

Earlier that day, a Humanitarian Record describing the missing person was created.

Meanwhile, other organizations have independently recorded additional humanitarian observations.

The family submits a humanitarian search using an HCP-compatible client.

At this moment:

- multiple Humanitarian Records may already exist;
- different organizations may have observed the same individual;
- no humanitarian interpretation has yet been performed.

The objective is to retrieve potentially relevant humanitarian observations.

---

# Humanitarian Query

The family provides the information currently available.

Illustrative search criteria include:

- reported name: María González;
- estimated age: approximately 74 years;
- last known location: Central Community Shelter;
- recognition features:
  - blue jacket;
  - small black backpack;
  - gray hair.

The corresponding Query is provided in:

```text
missing-person-query.json
```

---

# Search Execution

The HCP Node evaluates the Query against its available Humanitarian Records.

The search process may include:

- locally stored observations;
- synchronized observations from federation partners;
- recently received humanitarian observations.

Search retrieves Humanitarian Records that appear compatible with the Query.

Search does not evaluate whether those observations describe the same person.

---

# Search Results

Illustrative search results may include:

- Missing Person observation created by a family member;
- Hospitalized Person observation created by a hospital;
- Refugee Person observation created by a shelter;
- Found Person observation created by a volunteer.

These observations remain completely independent.

The search process does not establish relationships between them.

The corresponding example is provided in:

```text
search-results.json
```

---

# End of Search

The search operation ends after retrieving the available Humanitarian Records.

No Humanitarian Case has been created.

No humanitarian reasoning has been generated.

No correlation score exists.

The search result consists only of humanitarian observations.

```text
Query

        │

        ▼

Search

        │

        ▼

Humanitarian Records

        │

        ▼

END
```

The next architectural stage is Correlation.

---

# Why Search Stops Here

One of the fundamental architectural principles of HCP is the separation between retrieval and interpretation.

Search retrieves humanitarian observations.

Correlation interprets humanitarian observations.

Keeping these responsibilities independent improves:

- explainability;
- interoperability;
- implementation independence;
- organizational autonomy.

---

# Related Specifications

This example illustrates concepts defined by:

- HCP-0011 — Query Model
- HCP-0012 — Correlation Model
- HCP-0013 — Synchronization Model
- HCP-0018 — Search Protocol

---

# Summary

This example demonstrates how HCP retrieves humanitarian observations without attempting to determine humanitarian understanding.

The search process ends with a collection of Humanitarian Records.

Those observations may later become the input for local correlation.

Search retrieves evidence.

Correlation creates understanding.
