---
id: rfc-02
title: Technology Choices for OpenAsso
status: draft  
date: 2025-12-08  
authors: openasso
---
# RFC-02 — Technology Foundations for OpenAsso

## Purpose

This RFC defines the **technical foundations** of OpenAsso.  
It establishes the architectural principles, the high-level system design, and the main technology choices required to implement the functional scope defined in RFC-01.

It does not describe the database schema (will be discussed in [RFC-03]).

## Core Technology Principles

1. **Local-first**  
   The system must run entirely on a local machine, without relying on external services.

2. **Durability**  
   All data must use open, long-lived formats and remain accessible in the long term.

3. **Simplicity**  
   Installation, operation, and backups must be understandable by non-technical users.

4. **Maintainability**  
   The codebase must remain small, coherent, and easy to reason about over time.

## System Architecture

OpenAsso follows a **local web application + embedded database** design:

```
Browser (UI) → Local backend (API) → SQLite file
```

### Frontend

A local web application served by the backend.  
Runs in any modern browser and handles all user interactions.

### Backend

A lightweight local process exposing a small API surface.  
Implemented in **TypeScript**, running on **Deno**.  
Responsible for:

- database access,
- serving the frontend,
- exporting data (CSV/JSON),
- generating simple HTML documents.

### Storage

All data is stored in **SQLite**, in a single local database file.  
The SQLite file is the authoritative data source.

## Technology Choices

### Database: SQLite

Selected as the storage engine for its stability, portability, and suitability for local-first applications.

### Backend Runtime: Deno

The backend is executed locally using **Deno**, allowing:

- a self-contained runtime,
- native TypeScript support,
- future binary distribution.

### Backend Language: TypeScript

Chosen for consistency across the codebase and long-term maintainability.

### Frontend

A local web application built with a lightweight modern framework (framework choice does not impact RFC-02).  
Served directly by the backend.

### Document Generation

v1 uses **HTML with print styles** for all generated documents.  
Users may export PDFs using the browser’s native print-to-PDF feature.

No dedicated PDF engine is included in v1.

## Data Layout

Local file structure (indicative):

```
openasso/
  data/
    openasso.db
  exports/
    <exercise>/
      members.csv
      payments.csv
      memberships.csv
  config/
    association.yaml
```

## Out-of-scope for v1

To preserve simplicity, V1 does *not* include:

- multi-device sync,
- user accounts or permission models,
- hosting or cloud dependencies,
- encrypted remote backups,
- containerized deployments,
- HTTPS requirements (local usage only).

## Decisions

- OpenAsso is a **local-first** application with no external runtime dependencies.
- SQLite is the **sole data store**.
- The backend is written in **TypeScript**, executed via **Deno**.
- The frontend is a **local web application**, served by the backend.
- Document generation in v1 is **HTML-only** (print/PDF handled by the browser).
- A standalone binary distribution is a long-term objective.

## Relations to Other RFCs

- [RFC-01] defines the functional scope and core concepts.  
- [RFC-03] will specify the data model, the database schema and SQL queries for v1.

---

[RFC-01]: ./rfc-01-scope.md
[RFC-03]: ./