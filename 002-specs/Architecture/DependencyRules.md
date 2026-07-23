# Dependency Rules

Version: 1.0
Status: Approved

---

# Purpose

This document defines the permitted dependencies between solution projects.

Its purpose is to ensure:

- Zero cyclic references
- Stable architecture
- Independent modules
- Long-term maintainability

These rules are mandatory.

---

# Dependency Graph

```
                 Web
                  │
                  ▼
                 API
                  │
                  ▼
                 CLI
                  │
                  ▼
              Hosting
             /       \
            ▼         ▼
     Connectors   Extensions
            \       /
             ▼     ▼
              Engine
```

Dependencies SHALL always flow downward.

No reverse dependency is permitted.

---

# Project Dependency Matrix

| Project | May Reference |
|----------|---------------|
| Engine | None |
| Connectors | Engine |
| Extensions | Engine |
| Hosting | Engine, Connectors, Extensions |
| CLI | Hosting |
| API | Hosting |
| Web | API (HTTP only) |

---

# Engine Rules

Engine is the architectural center.

Engine SHALL NOT reference:

- Connectors
- Extensions
- Hosting
- CLI
- API
- Web

Engine SHALL remain technology-independent.

---

# Connector Rules

Connectors may reference:

- Engine

Connectors SHALL NOT reference:

- Hosting
- CLI
- API
- Web
- Extensions
- Other Connectors

Each connector shall be independent.

---

# Extension Rules

Extensions may reference:

- Engine

Extensions SHALL NOT reference:

- Connectors
- Hosting
- CLI
- API
- Web
- Other Extensions

Each extension shall be independent.

---

# Hosting Rules

Hosting is the only Composition Root.

Hosting may reference:

- Engine
- Connectors
- Extensions

Hosting SHALL own:

- Dependency Injection
- Plugin Discovery
- Plugin Registration
- Configuration
- Logging

---

# Host Rules

CLI and API SHALL reference only Hosting.

They SHALL contain no business logic.

---

# Web Rules

The Web application SHALL communicate through HTTP APIs only.

It SHALL NOT directly reference Engine.

---

# Cyclic References

Cyclic project references are strictly prohibited.

Every project graph shall remain a Directed Acyclic Graph (DAG).

---

# Plugin Independence

Adding a Connector or Extension SHALL NOT require modifications to Engine whenever reasonably possible.

---

# Review Rule

Any new project introduced into the solution must define:

- Why a new assembly is required.
- Why an existing project cannot own the responsibility.
- Its dependency direction.

Otherwise, the project shall not be created.