---
id: rfc-03
title: Technical Foundations
status: draft
date: 2025-12-09
authors: openasso
---

# RFC-03 — Technical Foundations

## 1. Purpose

This RFC defines the **technical principles and foundational decisions** guiding the implementation of OpenAsso.

It establishes the high-level framework within which all technical work must occur, including:

- how data is stored,
- how the application runs,
- the architectural constraints the project must respect.

This RFC does **not** describe the internal architecture of the application, the detailed data model, or the structure of the codebase.

## 2. Guiding Technical Principles

1. **Local-first by design**  
   The system must operate fully without internet access.  
   All core workflows must remain available offline.

2. **Single durable data file**  
   An association’s entire dataset must be stored in a single, inspectable, backup-friendly file.

3. **Open and long-lived formats**  
   Data must be readable in the future using standard tools, even without OpenAsso.

4. **Minimal operational complexity**  
   Volunteers with limited time and technical skills must be able to install, run, back up, and transfer the data.

5. **No vendor lock-in**  
   The system must avoid dependencies that centralize or externalize data or functionalities.

6. **Extensibility over time**  
   Technical choices must enable the future addition of modules (payments, synchronization, governance, etc.) without redesigning the foundation.

## 3. Core Technical Decisions

### 3.1 Persistence Layer

OpenAsso uses **SQLite** as its storage foundation.

Rationale:

- stable, battle-tested, and broadly supported,
- single-file database,
- suitable for offline use,
- combines durability with simplicity,
- guarantees that data remains readable through standard tooling.

### 3.2 Data Ownership Model

Each association corresponds to **one SQLite database file**.

This file is:

- the authoritative source of truth,
- directly portable (copy/paste),
- easily backupable,
- readable independently of OpenAsso.

No external service or cloud provider is required.

### 3.3 Execution Environment

OpenAsso runs as a **local application**, capable of serving a user interface on the same device.

Implementation details (web app, desktop wrapper, CLI, etc.) are out of scope, but the environment must:

- require no remote backend,
- support offline operation,
- remain lightweight and easy to deploy,
- allow future packaging options (single binary, desktop app, etc.).

### 3.4 Technology Stack Direction

The implementation will rely on **TypeScript** for both backend and frontend logic.

The preferred runtime for local execution is **Deno**, due to:

- built-in TypeScript support,
- integrated tooling,
- simple packaging capabilities.

This decision defines the technological direction without prescribing the application structure.

## 4. Architectural Constraints

The technical foundation must ensure that:

- all persistent operations go through the SQLite file,
- backups remain trivial (file copy, export),
- the system works deterministically offline,
- the runtime footprint remains small,
- dependencies are kept intentionally minimal,
- future features such as synchronization can be layered without altering core guarantees.

## 5. Out of Scope

The following are intentionally excluded from this RFC:

- detailed architecture (API shape, module boundaries),
- database schema or domain mapping ([RFC-04]),
- UI technologies or component models,
- authentication models,
- packaging/distribution formats,
- synchronization protocols.

These decisions belong to later RFCs.

## 6. Decision

OpenAsso adopts the following technical foundations:

- **SQLite** as the single durable, portable datastore,
- **one file = one association**,
- **local-first execution**, no external backend,
- **TypeScript** as the primary implementation language,
- **Deno** as the preferred runtime for local execution,
- a technical posture favoring **durability, simplicity, and autonomy**.

All future technical work must align with these principles and constraints.

[RFC-04]: ./rfc-04-model.md