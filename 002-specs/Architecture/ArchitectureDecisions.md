# Architecture Decisions (ADR)

Version: Living Document
Status: Active

---

# Purpose

This document records significant architectural decisions made during the development of BizTalkLens.

Unlike other architecture documents, this specification captures:

- Context
- Problem
- Decision
- Rationale
- Consequences

Future architectural changes SHALL update this document.

Architecture evolves through recorded decisions, not assumptions.

---

# ADR-001

## Title

Product-Oriented Solution Structure

### Status

Accepted

### Context

Traditional enterprise solutions are commonly organized using technical layers.

Examples include:

- Domain
- Application
- Infrastructure
- Presentation

While suitable for many business applications, this structure does not accurately represent the responsibilities of an Engineering Intelligence Platform.

BizTalkLens is fundamentally a platform that discovers, correlates, analyzes and understands enterprise integration environments.

### Decision

Organize the solution around product responsibilities.

```
Engine

Connectors

Extensions

Hosting

Hosts
```

### Consequences

Advantages

- Stable long-term architecture
- Easier navigation
- Product-focused organization
- Better separation of responsibilities

Trade-offs

- Clean Architecture moves inside modules instead of projects.

---

# ADR-002

## Title

Engine is Technology Independent

### Status

Accepted

### Context

The Engine contains the product intelligence.

External technologies evolve.

The business domain should not.

### Decision

Engine shall remain independent of:

- ExplorerOM
- SQL
- WMI
- Azure
- ASP.NET
- Console
- UI frameworks

### Consequences

Advantages

- Easier testing
- Easier evolution
- Easier migration
- Better portability

Trade-offs

Requires adapters for external systems.

---

# ADR-003

## Title

Hosting is the Composition Root

### Status

Accepted

### Context

Dependency Injection scattered across multiple projects becomes difficult to maintain.

Composition should exist in one place.

### Decision

Hosting is responsible for:

- Dependency Injection
- Configuration
- Logging
- Plugin Discovery
- Plugin Registration

CLI and API remain thin.

### Consequences

Advantages

- Single startup location
- Predictable dependency graph
- Easier maintenance

Trade-offs

Hosting becomes the runtime entry point.

---

# ADR-004

## Title

Connectors Collect Evidence Only

### Status

Accepted

### Context

Mixing collection with analysis creates tightly coupled systems.

### Decision

Connectors only acquire information.

They do not:

- Analyze
- Generate reports
- Produce recommendations
- Build documentation

### Consequences

Advantages

- Simple responsibilities
- Easier testing
- Easier extension

Trade-offs

Additional orchestration inside Engine.

---

# ADR-005

## Title

Extensions Consume Knowledge

### Status

Accepted

### Context

Generating documentation, diagrams and reports should not influence discovery.

### Decision

Extensions consume the Knowledge Graph.

They never collect information.

### Consequences

Advantages

- Better extensibility
- Independent outputs
- Independent deployment

Trade-offs

Knowledge model must remain stable.

---

# ADR-006

## Title

Behavior Before Implementation

### Status

Accepted

### Context

Architecture should implement agreed product behavior.

Implementation should not define product behavior.

### Decision

BizTalkLens follows:

BDD

↓

DDD

↓

Clean Architecture

↓

Implementation

Behavior defines the product.

The domain models the product.

Architecture implements the product.

### Consequences

Advantages

- Better communication
- Better specifications
- Better testing

Trade-offs

Requires stronger product specifications.

---

# ADR-007

## Title

Projects Represent Stable Boundaries

### Status

Accepted

### Context

Many solutions create projects for every layer.

This leads to dozens of small assemblies with little architectural value.

### Decision

Projects exist only when they represent stable runtime or deployment boundaries.

Modules represent business capabilities.

### Consequences

Advantages

- Smaller solution
- Easier navigation
- Better maintainability

Trade-offs

Projects become larger than traditional layered solutions.

---

# ADR-008

## Title

No Cyclic Dependencies

### Status

Accepted

### Context

Cyclic project references eventually produce architectural erosion.

### Decision

The solution dependency graph shall remain a Directed Acyclic Graph (DAG).

Every dependency points toward Engine.

No project references back upward.

### Consequences

Advantages

- Predictable architecture
- Easier refactoring
- Better testing

Trade-offs

Requires careful dependency management.

---

# ADR-009

## Title

Internal Clean Architecture

### Status

Accepted

### Context

Clean Architecture remains valuable.

However, it should not define the repository structure.

### Decision

Clean Architecture exists inside product modules.

Example

```
Discovery/

    Domain/

    Application/

    Infrastructure/
```

instead of

```
Solution/

    Domain/

    Infrastructure/

    Application/
```

### Consequences

Advantages

- Product-first navigation
- Familiar engineering practices
- Better modularity

Trade-offs

Requires discipline within modules.

---

# ADR-010

## Title

Architecture Stability

### Status

Accepted

### Context

The product is expected to evolve for many years.

Implementation technologies will change.

### Decision

Solution architecture should remain stable.

Frameworks may change.

Languages may change.

UI technologies may change.

The architectural responsibilities should remain unchanged.

### Consequences

Advantages

- Long-term maintainability
- Easier upgrades
- Easier onboarding
- Consistent mental model

Trade-offs

Architecture changes require deliberate review rather than convenience.