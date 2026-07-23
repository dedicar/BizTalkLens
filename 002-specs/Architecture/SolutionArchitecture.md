# BizTalkLens Solution Architecture

Version: 1.0
Status: Approved
Owner: Product Engineering

---

# Purpose

This document defines the immutable solution architecture of BizTalkLens.

It establishes:

- Solution structure
- Project responsibilities
- Dependency rules
- Internal architecture guidance
- Engineering principles

This specification SHALL be considered the architectural constitution of the source code.

---

# Architectural Philosophy

BizTalkLens is an Engineering Intelligence Platform.

It is NOT a CRUD application.

It is NOT an ERP.

It is NOT a typical line-of-business system.

Its primary responsibility is to:

- Discover
- Collect
- Normalize
- Correlate
- Analyze
- Understand
- Document
- Recommend

across heterogeneous enterprise integration environments.

Therefore, the solution is organized around **product responsibilities**, not technical layers.

---

# Solution Structure

```
BizTalkLens.sln

src/

├── BizTalkLens.Engine                 (.NET Class Library)
│
├── BizTalkLens.Connectors             (.NET Class Library)
│
├── BizTalkLens.Extensions             (.NET Class Library)
│
├── BizTalkLens.Hosting                (.NET Class Library)
│
├── BizTalkLens.Cli                    (.NET Console)
│
├── BizTalkLens.Api                    (.NET ASP.NET Core Web API)      (Future)
│
└── BizTalkLens.Web                    (React/Vite or Blazor)           (Future)

tests/

└── BizTalkLens.Tests                  (.NET xUnit)
```

---

# Project Responsibilities

## Engine

The heart of BizTalkLens.

Responsible for:

- Discovery orchestration
- Evidence model
- Knowledge graph
- Correlation
- Analysis
- Documentation generation
- Reporting
- Recommendations
- Business rules
- Domain model

The Engine SHALL NOT know anything about:

- ExplorerOM
- SQL
- WMI
- BizTalk360
- ASP.NET
- Console
- React
- Blazor

The Engine must remain technology-independent.

---

## Connectors

Responsible for acquiring information from external systems.

Examples:

- ExplorerOM
- SQL Server
- BizTalk360
- PowerShell
- WMI
- IIS
- Windows
- Certificates
- File System
- Azure
- Service Bus
- SAP
- RabbitMQ
- Kafka

Connectors SHALL ONLY collect evidence.

They SHALL NOT perform:

- Analysis
- Reporting
- Documentation
- Recommendations

---

## Extensions

Responsible for producing value from the Knowledge Graph.

Examples:

- Word
- PDF
- HTML
- Markdown
- Mermaid
- PlantUML
- CSV
- Excel
- Power BI
- AI Prompt Export
- Architecture Reports
- Migration Advisors

Extensions SHALL consume knowledge.

They SHALL NOT collect evidence.

---

## Hosting

Hosting is the Composition Root.

Responsibilities include:

- Dependency Injection
- Configuration
- Logging
- Plugin Discovery
- Plugin Loading
- Workflow Registration
- Telemetry
- Caching
- Options
- Feature Flags

Hosting wires the application together.

---

## CLI

Responsible only for:

- Commands
- Console UX
- Progress
- Exit Codes

No business logic belongs here.

---

## API (Future)

Responsible only for:

- REST
- Controllers
- Swagger
- Authentication
- Authorization
- SignalR

---

## Web (Future)

Responsible only for:

- User Interface
- Visualization
- Interaction

Business logic SHALL remain inside Engine.

---

# Dependency Graph

```
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
```

The solution dependency graph SHALL remain acyclic.

---

# Project References

```
Engine
    references nothing

Connectors
    -> Engine

Extensions
    -> Engine

Hosting
    -> Engine
    -> Connectors
    -> Extensions

CLI
    -> Hosting

API
    -> Hosting

Web
    -> API (HTTP only)
```

No additional project references are permitted without architectural review.

---

# Internal Architecture

Projects define product boundaries.

Modules define business capabilities.

Inside Engine:

```
Engine

Discovery/
    Domain/
    Application/
    Infrastructure/

Knowledge/
    Domain/
    Application/
    Infrastructure/

Analysis/
    Domain/
    Application/
    Infrastructure/

Documentation/
    Domain/
    Application/
    Infrastructure/

Reporting/
    Domain/
    Application/
    Infrastructure/

Recommendation/
    Domain/
    Application/
    Infrastructure/
```

The same approach may be adopted inside Connectors and Extensions where appropriate.

---

# Engineering Principles

## Product First

Projects SHALL represent product responsibilities, not technical layers.

---

## BDD First

Product capabilities SHALL begin as behavioral specifications.

Behavior defines implementation.

---

## DDD Second

Domain models SHALL represent the engineering concepts of BizTalkLens.

Examples include:

- Discovery Session
- Evidence
- Artifact
- Endpoint
- Relationship
- Knowledge Graph

---

## Clean Architecture Inside Modules

Clean Architecture, Onion Architecture, CQRS, Vertical Slice, and SOLID are implementation techniques.

They SHALL be applied inside modules, not as the solution structure.

---

## Immutable Dependencies

Project references SHALL always flow in one direction.

No cyclic references are permitted.

---

## Composition Root

Hosting SHALL be the only project responsible for application composition.

Dependency Injection SHALL NOT be configured elsewhere.

---

## Thin Hosts

CLI, API, and Web SHALL contain no business logic.

They are delivery mechanisms only.

---

## Pluggable Architecture

New Connectors and Extensions SHALL be added without modifying the Engine whenever possible.

---

## Technology Independence

The Engine SHALL remain independent of:

- UI frameworks
- Databases
- Communication protocols
- External SDKs
- Infrastructure technologies

---

## Long-Term Stability

This solution architecture is intended to remain stable for the lifetime of the product.

Implementation patterns may evolve.

Project responsibilities shall remain stable.