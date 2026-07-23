# BizTalkLens Source Code

> **Purpose**
>
> This directory contains the complete implementation of BizTalkLens.
>
> The source code is organized around **business capabilities**, not technical layers.
> Each capability encapsulates its own domain, application, infrastructure and contracts while participating in the overall product workflow.
>
> This document is normative. All source code shall conform to the architecture and dependency rules defined herein.

---

# Source Architecture Vision

BizTalkLens is built as a modular, capability-driven application.

The architecture shall:

- Mirror the business workflow.
- Isolate capabilities.
- Keep the core independent of hosting technology.
- Support CLI today.
- Support Web API and React/Vite UI in the future.
- Allow new collectors and recommendation targets without architectural changes.

---

# Product Runtime

```
                    Existing BizTalk Environment
                                 │
     ┌───────────────┬────────────┴─────────────┬──────────────┐
     │               │                          │              │
 ExplorerOM        SQL Server              PowerShell       BizTalk360
     │               │                          │              │
     └───────────────┴──────────────┬───────────┴──────────────┘
                                    │
                             Collector Layer
                                    │
                                    ▼
                           Discovery Engine
                                    │
                                    ▼
                          Evidence Repository
                                    │
                                    ▼
                         Knowledge Graph Builder
                                    │
                                    ▼
                           Knowledge Repository
                                    │
        ┌──────────────┬────────────┼──────────────┬──────────────┐
        ▼              ▼            ▼              ▼              ▼
    Analysis     Documentation   Reporting     Diagrams     Recommendation
                                    │
                                    ▼
                                 CLI Host
```

The Knowledge Repository is the heart of BizTalkLens.

Every downstream capability consumes knowledge instead of directly querying collectors.

---

# Architectural Principles

The implementation follows:

- Capability Driven Architecture
- Clean Onion Architecture
- Domain Driven Design (DDD)
- CQRS where appropriate
- Dependency Injection
- SOLID Principles
- Modular Monolith

---

# Capability Architecture

The solution is organized around the following capabilities.

```
Workspace

Collectors

Discovery

Knowledge

Analysis

Documentation

Reporting

Diagram

Recommendation

Hosting

Shared
```

Each capability owns its own implementation.

---

# Internal Capability Structure

Every capability follows the same internal architecture.

```
Capability

├── Application
├── Domain
├── Infrastructure
└── Contracts
```

Responsibilities:

- **Domain** — Business model and rules
- **Application** — Use cases, CQRS handlers, orchestration
- **Infrastructure** — External integrations and persistence
- **Contracts** — Public interfaces and shared models

---

# Solution Structure

```
003-src/

Shared/
    Common components
    Cross-cutting concerns

Workspace/

Collectors/

Discovery/

Knowledge/

Analysis/

Documentation/

Reporting/

Diagram/

Recommendation/

Hosting/
    Cli/
    WebApi/          (Future)

UI/
    React/           (Future)
```

Each top-level directory represents a business capability.

---

# Collector Architecture

Collectors acquire evidence from external sources.

Supported collectors include:

- ExplorerOM
- SQL Server
- PowerShell
- WMI
- BizTalk360
- Binding Files
- MSI Packages
- IIS
- Windows
- File System
- Certificates

Additional collectors may be introduced without modifying existing capabilities.

Collectors do not perform analysis.

---

# Engine Responsibilities

### Discovery Engine

Coordinates collectors and produces normalized evidence.

### Knowledge Engine

Transforms evidence into a unified knowledge model.

### Analysis Engine

Produces findings from the knowledge graph.

### Documentation Engine

Generates business and technical documentation.

### Reporting Engine

Produces operational, architectural and management reports.

### Diagram Engine

Generates visual representations including Mermaid diagrams.

### Recommendation Engine

Evaluates modernization options against the knowledge graph.

---

# Knowledge Repository

The Knowledge Repository is the central source of truth.

It maintains:

- Applications
- Artifacts
- Relationships
- Dependencies
- Infrastructure
- Interfaces
- Integration topology

All downstream capabilities consume knowledge from this repository.

---

# Recommendation Strategy

Supported modernization targets:

- Azure Integration Services
- IBM webMethods
- InterSystems IRIS

Recommendations shall be evidence-based.

If the selected target cannot adequately support the existing solution, BizTalkLens shall explicitly reject the recommendation and provide the reasons.

---

# Dependency Direction

Business dependency shall always flow forward.

```
Collectors
      │
      ▼
Discovery
      │
      ▼
Knowledge
      │
      ▼
Analysis
      │
 ┌────┼────────────┐
 ▼    ▼            ▼
Docs Reports   Diagrams
      │
      ▼
Recommendation
```

Technical dependencies shall always point inward according to Clean Onion Architecture.

Circular dependencies are prohibited.

---

# Hosting

Current Host

- CLI

Future Hosts

- Web API
- React/Vite UI

Hosting technologies shall remain thin and contain no business logic.

Business capabilities shall remain host-independent.

---

# Testing

Each capability shall have corresponding:

- Unit Tests
- Integration Tests
- Architecture Tests

Testing follows the same capability boundaries as implementation.

---

# Extension Model

BizTalkLens is designed for extension.

New collectors, engines, recommendation targets and hosts should be added without modifying existing business capabilities.

The preferred extension mechanism is through well-defined contracts and dependency injection.

---

# Source Code Roadmap

```
Capability
      │
      ▼
Specification
      │
      ▼
Implementation
      │
      ▼
Tests
```

Source code shall always remain aligned with the product architecture and engineering specifications defined elsewhere in the repository.

---

# Dependency Graph

                 +----------------+
                 |      Web       |
                 +-------+--------+
                         |
                         v
                 +----------------+
                 |      API       |
                 +-------+--------+
                         |
                         v
                 +----------------+
                 |      CLI       |
                 +-------+--------+
                         |
                         v
                 +----------------+
                 |    Hosting     |
                 +---+--------+---+
                     |        |
         +-----------+        +------------+
         |                             |
         v                             v
+-------------------+          +--------------------+
|    Connectors     |          |    Extensions      |
+---------+---------+          +----------+---------+
          \                              /
           \                            /
            \                          /
             +-----------+------------+
                         |
                         v
                 +----------------+
                 |     Engine     |
                 +----------------+
