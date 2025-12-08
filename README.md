# OpenAsso

**OpenAsso** is a local-first, durable, and vendor-independent administration tool for associations.  
It helps organizations manage their people, memberships, and payments with full data ownership.

OpenAsso is designed for associations that need a modern tool without relying on SaaS platforms.

## Core Principles

- **Local-first**: all data stays on the user's machine
- **Durable**: SQLite as the single source of truth
- **Simple**: easy installation, easy backups, minimal dependencies
- **Vendor-neutral**: no cloud services, no lock-in
- **Open Source**: transparent design, extensible over time

## What OpenAsso Provides (v1)

- Manage **persons** (members, legal guardians, volunteers)
- Track **exercises** (annual periods)
- Record **memberships** for each exercise
- Register **payments** made by members or guardians
- Generate **lists** and **basic payment certificates**

This core feature set is intentionally limited to keep the tool reliable and easy to adopt.

## Project Structure

```
openasso/
├── rfc/         # Formal decision documents (functional & technical)
├── archi/       # Architecture diagrams and system views
├── docs/        # User and admin documentation
└── ...          # To be defined
```

## License

MIT Licence.
