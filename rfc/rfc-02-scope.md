---
id: rfc-02
title: Functional Scope & V1 Definition
status: draft
date: 2025-12-09
authors: openasso
---

# RFC-02 — Functional Scope & V1 Definition

## 1. Purpose

This RFC defines:

1. The **functional scope** of the OpenAsso service (what the service aims to support in general).
2. The **functional perimeter of v1**, identifying the minimal set of capabilities that make the tool usable by real associations.

This RFC does **not** define:
- the internal data model,
- technical choices,
- implementation mechanisms,
- terminology for storage or computation.

It describes *what users must be able to do*, not how the system represents it.

## 2. Rationale

[RFC-01] shows that associations share a recurring set of administrative needs:

- managing contacts (individuals and organizations),
- handling minors and legal guardians,
- managing activities or programs,
- maintaining yearly administrative cycles,
- determining who is a member,
- producing basic administrative documents.

OpenAsso must therefore provide a **clear, durable functional baseline**, suitable for a large spectrum of associations.

## 3. Core Functional Scope (Service-Level)

The long-term service scope includes all functional abilities that associations commonly require.  
These capabilities define the *ambition* of OpenAsso, not the deliverable of v1.

### 3.1 Contact & Relationship Management

The service must support:
- storing and maintaining individuals and organizations,
- identifying minors,
- linking minors with their legal guardians,
- managing partners, sponsors, funders, public institutions,
- keeping administrative information consistent across years.

### 3.2 Activity / Program Management

The service must allow associations to:
- define activities, courses, or programs,
- associate participants with activities,
- understand which activities confer association membership,
- generate participant listings,
- support multiple activities per person.

### 3.3 Yearly Administrative Cycles

The service must enable:
- creating and naming yearly exercises,
- reviewing past exercises,
- associating activities and memberships with a specific year,
- generating summaries for each cycle.

### 3.4 Membership Management

The service must allow associations to:
- determine who is a member for a given year,
- reflect situations where membership results from participation in activities,
- handle exceptional cases where someone is considered a member without participating in activities (e.g., volunteers, board members).

### 3.5 Documents & Exports

The service must support:
- producing member lists,
- producing activity participant lists,
- generating administrative confirmations required by families or institutions.

### 3.6 Payments & Financial Tracking

The service must allow associaitons to:
- record payments,
- identify the payer,
- produce payment certificates.

## 4. Functional Scope for v1

v1 focuses on delivering **immediate administrative value** while keeping the system simple and durable.

### 4.1 v1 Objectives

V1 should allow an association to:
- manage its contacts,
- organize its activities for a given year,
- record who participates in which activity,
- determine who is considered a member,
- handle exceptions to membership,
- export basic administrative documents.

### 4.2 v1 Core Capabilities

#### 4.2.1 Manage Contacts

Users must be able to:
- create, update, and archive individuals and organizations,
- identify minors by birthdate,
- specify one or more legal guardians for minors.

#### 4.2.2 Manage Activities

Users must be able to:
- create and manage activities offered during a given year,
- indicate whether an activity confers membership,
- associate participants with activities,
- list participants by activity.

#### 4.2.3 Manage Yearly Cycles

Users must be able to:
- create and activate a yearly exercise,
- consult previous exercises,
- navigate all information per exercise.

#### 4.2.4 Determine Membership

v1 must allow:
- identifying members based on participation in activities that confer membership,
- marking individuals as members manually for exceptional cases (volunteers, board members, honorary participants),
- listing all members for the current exercise.

#### 4.2.5 Produce Documents

Users must be able to:
- export the member list for a year,
- export participant lists for activities,
- generate simple membership confirmations.

### 4.3 Explicitly Out of Scope for v1

The following are intentionally excluded:

- payment tracking of any kind,
- fee calculation or financial summaries,
- attendance tracking,
- coach or teacher management,
- scheduling or time-slot management,
- dashboards or analytics,
- communication tools (email, messaging),
- governance or AG workflows.

## 5. Discussion Points

The following may be refined in future RFCs:

- the level of detail associated with activities (pricing, age restrictions, schedule),
- how exercises relate to recurring data,
- how membership exceptions are reviewed across years,
- integration of financial features.

## 6. Decision

OpenAsso will adopt:

1. The **functional service scope** described in section 3 as its long-term target.
2. The **v1 perimeter** described in section 4 as the minimal foundation.
3. A membership approach that supports both:
   - membership derived from activity participation,
   - manual membership designation for exceptional cases.

This provides a simple, realistic, and extensible functional baseline aligned with [RFC-01].

[RFC-01]: ./rfc-01-context.md