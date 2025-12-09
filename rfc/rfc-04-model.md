---
id: rfc-04
title: Domain Model (V1)
status: draft
date: 2025-12-09
authors: openasso
---

# RFC-04 — Domain Model (V1)

## 1. Purpose

This RFC defines the **domain model** of OpenAsso for the v1 scope.

It synthesizes:
- the environment and constraints described in [RFC-01],
- the functional perimeter described in [RFC-02],
- the technical foundations described in [RFC-03],

to propose a **coherent set of business entities** that the system must represent.

This RFC does **not** specify storage details, SQL structure, API design, or UI mechanisms.

It answers the question:

> *Which business concepts must the system formally represent in the v1,  
and how do they relate to each other?*

## 2. Domain Modeling Approach

The model reflects the operational reality of associations:

1. **People and organizations must be identified clearly.**
2. **The yearly cycle structures all administrative operations.**
3. **Activities define what the association offers each year.**
4. **Registration expresses participation in these activities.**
5. **Membership expresses belonging to the association for a given year.**

The v1 model remains intentionally simple while capturing the core mechanisms associations rely on.

## 3. Business Entities (v1)

The domain model for v1 consists of five entities:

- **Contact**
- **Exercise**
- **Activity**
- **Registration**
- **Membership**

These entities form the minimal backbone of association administration in the v1 scope.

No additional entities (e.g., payments, attendance, sections, relationships) are included in v1, as they fall outside the functional perimeter of [RFC-02].

## 4. Entity Definitions

### 4.1 Contact

A **Contact** represents any individual or organization interacting with the association.

It may correspond to:
- adult participants,
- minors,
- legal guardians,
- volunteers,
- board members,
- external organizations involved in administrative or financial processes.

A Contact:
- exists independently of exercises,
- may accumulate registrations over several years,
- may be designated as a member manually when required.

The v1 model does not distinguish technical relationship types;  
the link between minors and guardians is treated functionally, not structurally.

### 4.2 Exercise

An **Exercise** represents a yearly administrative period.

It provides the temporal frame for:
- the list of activities offered that year,
- the registrations associated to those activities,
- the membership list for that year.

Key properties:
- Exercises are created annually.
- Once closed, they serve as historical snapshots.
- All V1 business data except Contacts is scoped to an Exercise.

### 4.3 Activity

An **Activity** is a course, program, workshop, or section offered during a specific Exercise.

Characteristics:
- belongs to a single Exercise,
- defines an offering (e.g., Karate adultes, Body-fight, Stage d'été),
- determines whether participating in it implies membership in the association (functional rule per [RFC-02]).

Each exercise defines its own set of Activities.

### 4.4 Registration

A **Registration** links a Contact to an Activity within an Exercise.

It expresses that:
> “This contact is registered in this activity for this administrative year.”

Registrations are used to:
- build participant lists,
- support administrative reporting,
- determine membership when applicable,
- generate certificates or summary documents.

A Contact may have several Registrations within the same Exercise.

### 4.5 Membership

A **Membership** expresses that a Contact is considered a member of the association for a given Exercise.

Membership may reflect:
- participation in activities that imply membership,
- administrative rules specific to the association,
- manual designation (e.g., volunteers, board members).

Key points:
- Membership is scoped per Exercise.
- It represents association-level belonging, not activity-level enrollment.
- The rules determining membership (derived or manual) are defined in [RFC-02] and are not repeated here.

---

## 5. Conceptual Relationships (High-Level)

```
Exercise
  ├── defines → Activities
  │        └── receives → Registrations (Contact ↔ Activity)
  └── contains → Memberships (Contact ↔ Exercise)

Contacts
  └── appear in → Registrations and Memberships
```

Interpretation:

- Contacts exist independently of exercises.
- Each exercise defines its own Activities.
- Contacts register for Activities through Registrations.
- Membership reflects association-level belonging for an Exercise.

This model captures the essential administrative flows of associations.

## 6. Cross-Entity Considerations

### 6.1 Temporal Boundaries

- Contacts are persistent across all years.
- Activities, Registrations, Memberships are scoped to a single Exercise.

### 6.2 Independence of Exercises

Data from one exercise does not alter another.  
Associations can compare or export past years independently.

### 6.3 Simplicity and Extensibility

The model intentionally avoids introducing:

- payment entities,
- attendance,
- pricing structures,
- guardian/child relationship entities,
- sections or groups,

because they fall outside the V1 functional perimeter and would add structural complexity prematurely.

Future RFCs may extend the model with additional entities.

## 7. Decision

OpenAsso adopts the domain model defined above for the v1 scope:

- **Contacts** represent people and organizations.
- **Exercises** structure the administrative lifecycle.
- **Activities** define the yearly offer.
- **Registrations** express participation.
- **Memberships** express association-level belonging.

This model is coherent with the operational context of associations,  
consistent with the functional perimeter,  
and compatible with the technical foundations of the project.

[RFC-01]: ./rfc-01-context.md
[RFC-02]: ./rfc-02-scope.md
[RFC-03]: ./rfc-03-foundations.md