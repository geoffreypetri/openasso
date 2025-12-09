---
id: rfc-01
title: System Context & Problem Definition
status: draft
date: 2025-12-09
authors: openasso
---

# RFC-01 — System Context & Problem Definition

## 1. Purpose

This RFC defines the **system context** of OpenAsso:  
the environment in which associations operate, the actors involved, the administrative processes they must handle, and the structural constraints shaping their digital needs.

It does **not** define what OpenAsso will implement.  
It establishes the *problem space*, not the *solution*.

## 2. Overview of the Association Landscape

Associations operate with:

- limited administrative resources,
- heterogeneous digital skills,
- frequent turnover among volunteers and board members,
- obligations toward public institutions and participants.

Despite their diversity, most associations share a similar administrative backbone:

- they collect and manage participant information,
- they organize activities or programs,
- they structure their work around yearly cycles (“exercises”),
- they collect membership fees or participation fees,
- they produce administrative documents,
- they maintain relationships with external organizations.

Any long-term tool must reflect these realities.

## 3. Actors

Associations interact with a wide ecosystem of internal and external actors.

### 3.1 Internal Actors

- **Members**: individuals participating in the association.
- **Minors**: members under legal age requiring adult representation.
- **Legal guardians**: adults responsible for minors (administrative and financial).
- **Volunteers**: operational or administrative helpers.
- **Board members**: president, treasurer, secretary; responsible for compliance and continuity.
- **Teachers / coaches / facilitators**: operational contributors leading activities.
- **Committees / councils**: governance structures (depending on the association’s size).

### 3.2 External Actors

- **Municipalities and public authorities**: may provide facilities, funding, or require reports.
- **Federations / leagues / unions**: may require member lists or licensing information.
- **Funding bodies** (CAF, institutions, employers): may request certificates or participation proof.
- **Companies / sponsors / partners**: may fund activities or pay on behalf of participants.
- **Other associations or networks**: collaboration, shared events, resource pooling.

Actors may be **individuals** or **organizations**; both may interact financially or administratively.

## 4. Core Administrative Processes

Regardless of their specific mission, most associations manage recurring processes.

### 4.1 Contact and Participant Management

- Collecting identity and contact information.
- Maintaining up-to-date records.
- Identifying minors and their legal representatives.
- Managing organizations involved as partners, sponsors, or payers.

### 4.2 Activity / Program Management

- Defining programs, courses, workshops, or sections.
- Associating participants with specific activities.
- Determining which activities imply association membership.
- Managing teachers or facilitators.

### 4.3 Membership Management

- Determining who is a member for a given exercise.
- Handling membership fees or administrative requirements.
- Managing exceptions or reduced fees depending on activity or status.

### 4.4 Payment and Financial Tracking

- Receiving payments (cash, check, transfer, card).
- Identifying the payer (individual or organization).
- Allocating payments to membership or activity fees.
- Producing payment certificates or supporting documents.
- Reporting aggregated information to the board or institutions.

### 4.5 Exercise (Yearly Cycle) Management

- Opening and closing administrative years.
- Carrying over information from previous years.
- Generating lists, statistics, or summaries.

### 4.6 Document and Compliance Requirements

- Member lists, attendance sheets, insurance documents, proof of payment.
- Reports for municipalities, federations, or funding bodies.
- Annual general meeting (AG) documentation:
  - convocations,
  - minutes,
  - voting records,
  - yearly reports.

### 4.7 Administrative Continuity

- Transferring responsibility during board turnover.
- Ensuring readability of data years later.
- Maintaining consistent archives across changes in volunteers or tools.

## 5. Structural Constraints

Associations face constraints that strongly influence digital systems.

### 5.1 Organizational Constraints

- **High turnover**: board members and volunteers change often.
- **Limited time**: administrative workload must remain minimal.
- **Variable digital skills**: tooling must be simple and robust.

### 5.2 Legal and Practical Constraints

- Minors must be linked with legal guardians.
- Payments must be traceable for institutions or refunds.
- Documents may be requested years after the fact.
- Some data must remain archived long-term.

### 5.3 Technical Constraints

- Tools must be usable offline and without service dependencies.
- Backups must be trivial to perform and restore.
- Data must be stored in **open, durable, vendor-independent formats**.
- The system must tolerate inconsistent or partial data entry.

### 5.4 Longevity Constraints

- Associations need tools that survive:
  - board transitions,
  - device changes,
  - tool abandonment by vendors,
  - technological shifts.

Durability is a first-class requirement.

## 6. Problem Statement

Associations typically rely on:

- spreadsheets,
- paper forms,
- informal communication channels,
- fragmented tools,
- SaaS solutions that introduce cost, complexity, or lock-in.

This results in:

- data loss across years,
- difficulty maintaining continuity,
- inconsistent administrative records,
- heavy reliance on individual volunteers,
- challenges producing required documents,
- vulnerability to turnover.

A tool is needed that:

- matches real association workflows,
- supports both individuals and organizations,
- handles yearly cycles, memberships, activities, and payments,
- remains simple, durable, offline-capable, and transferable.

This is the problem space that OpenAsso must address.

## 7. Out of Scope

This RFC does **not** define:

- functional priorities or the V1 scope,
- domain concepts or data structures,
- technology choices,
- interaction design or UI models.

## 8. Decision

This RFC establishes the **complete system context** within which OpenAsso will evolve.  
Future RFCs must derive their functional and technical decisions from the actors, processes, objectives, and constraints described above.