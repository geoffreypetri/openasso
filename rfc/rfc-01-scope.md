---
id: rfc-01
title: Vision and Functional Scope of OpenAsso
status: draft  
date: 2025-12-08  
authors: openasso
---
# RFC-01 — Vision and Functional Scope of OpenAsso

## What is OpenAsso? Who is it for?

OpenAsso is a **simple, local-first, durable** management tool for associations that need to:

- keep a clean record of their **people** (members, legal guardians, volunteers...),
- manage **annual memberships**,
- track **payments**,
- generate **lists** and **basic certificates**,
- while remaining fully independent from SaaS platforms and vendors lock-in.

Primary users:

- the **board** (president, treasurer, secretary),  
- **volunteers** handling registrations and administrative tasks.

OpenAsso is an **internal management tool** — not a member-facing system.

## What needs does OpenAsso address? What does that imply in terms of entities?

Across many types of associations (sports, cultural, charity, school...),  
the following needs are:

### Identify people

-> **Person**  
A single object representing anyone involved in the association: members, legal guardians, volunteers, or payers.

### Support minors and legal guardians

Associations must be able to declare, for any minor Person,  
one or more other Person objects as **legal guardians** and potential payers.

*(Note: this relationship is functional; the technical representation — fields vs. link table — will be discussed in [RFC-03].)*

### Organize activity by exercise (annual administrative period)

-> **Exercise**  
Associations operate by season or annual cycle.

### 2.4 Track who is a member during a given exercise

-> **Membership**  
A Person may be (or not be) a member for a given Exercise, with an expected fee.

### Track payments

-> **Payment**  
Payments made by a Person (member or guardian) toward a membership.

### Produce simple documents

Lists of members, proof-of-payment certificates, documents referencing legal guardians when applicable.

*(No dedicated document entity is required in v1: documents are generated on the fly).*

## Functional core for v1

The v1 scope is intentionally **minimal**, but immediately useful for real associations.

### People management (Person)

- create / update / archive a person
- store essential contact information
- distinguish minors from adults (via date of birth)
- reference persons who are not members (e.g., guardian-only)

### Legal guardian relationships

- declare one or several adult Persons as legal guardians of a minor
- identify the payer (guardian or member) for a given membership
- ensure documents for minors display the correct legal guardian information

### Exercises (Exercise)

- create an exercise (e.g. *2025–2026*)
- set the current exercise
- access past exercises

### Memberships (Membership)

- attach a Person to an Exercise as a member
- define the expected amount (membership fee)
- track simple status: *member / not a member / pending*
- list members for an exercise

### Payments (Payment)

- record a payment (amount, date, method, reference)
- link the payment to a Person and an Exercise
- compute, for each Person and Exercise:
  - expected amount
  - total paid
  - outstanding balance

### Essential documents

- list of members for an Exercise
- simple proof-of-payment certificate:
  - for adults → in their own name
  - for minors → issued under the legal guardian’s name

## High-level outlook (future extensions, not part of v1)

OpenAsso may later evolve in these directions:

### Programs & registrations

Activities, workshops, events; per-program registrations; detailed pricing.

### Households & family structures

Group multiple Persons into a household for billing or communication.

### Governance

AG documents, mandates, roles, transparency features.

### Personalization & interoperability

Templates, tags, import/export, accounting exports.

These extensions do not affect v1’s simplicity or its data model.

## Decisions recorded

- OpenAsso’s v1 is built on **four functional objects**:  
  **Person**, **Exercise**, **Membership**, **Payment**.
- Minor–guardian relationships are part of the **v1 functional scope**,
  and rely on **Person ↔ Person** links (exact representation defined in [RFC-03]).
- No additional entities are required to deliver a useful v1.

## Relations to Other RFCs

- [RFC-02] will define the technology choices that support this functional scope.
- [RFC-03] will describe the data model and SQL schema for the v1.

---

[RFC-02]: ./rfc-02-technology-choices.md
[RFC-03]: ./