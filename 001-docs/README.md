# BizTalkLens Documentation

> **Purpose**
>
> This directory defines the documentation architecture of BizTalkLens.
> It establishes how product knowledge is organized, maintained, evolved, and consumed throughout the lifecycle of the project.
>
> This document is normative. All documentation within this repository shall conform to the principles and structure defined herein.

---

# Documentation Vision

BizTalkLens documentation shall describe the product from multiple perspectives while maintaining a single source of truth.

Documentation must enable:

- Product understanding
- Architectural understanding
- Engineering implementation
- AI-assisted development
- Long-term maintainability

Documentation shall evolve with the product and remain traceable to implementation.

---

# Documentation Principles

The documentation ecosystem shall follow these principles:

- Product First
- Capability Driven
- Single Source of Truth
- Progressive Refinement
- Traceability
- Separation of Concerns
- AI Friendly
- Version Controlled

---

# Documentation Hierarchy

```
Product
    │
    ▼
Engineering Documentation
    │
    ▼
Engineering Specifications
    │
    ▼
Source Code
    │
    ▼
Tests
```

Each level depends only on the level above.

Implementation shall never become the source of truth.

---

# Repository Documentation Structure

```
000-product/
    Product vision
    Business concepts
    Domain model
    Architecture
    Glossary

001-docs/
    Engineering documentation
    Standards
    Repository guidance
    Architetcure
    Architectural decisions

002-specs/
    Engineering specifications
    Capability specifications
    Component specifications
    Technical contracts

003-src/
    Source code
```

---

# Documentation Categories

## Product

Describes **what** BizTalkLens is.

Examples

- Vision
- Product Architecture
- Domain Model
- Terminology

---

## Documentation

Describes **how** the product should be engineered.

Examples

- Solution Architecture
- Coding Standards
- Testing Strategy

---

## Specifications

Describe **how each capability shall be implemented**.

Examples

- Discovery
- Knowledge
- Analysis
- Reporting
- Recommendation

---

## Source

Contains the implementation.

Documentation shall never be duplicated inside source code.

---

# Documentation Relationships

```
Vision

↓

Architecture

↓

Specifications

↓

Implementation

↓

Tests
```

Every implementation should be traceable back to a specification.

Every specification should trace back to product documentation.

---

# Documentation Standards

Every document should define:

- Purpose
- Scope
- Responsibilities
- Dependencies
- References
- Version

Documentation should avoid implementation details unless the document is specifically intended for engineering implementation.

---

# AI Documentation Guidelines

AI-generated documentation shall:

- preserve terminology
- avoid duplicated information
- reference existing documents
- maintain hierarchy
- expand existing structures rather than replace them
- keep documentation consistent across the repository

---

# Documentation Governance

The documentation ecosystem shall remain:

- Consistent
- Traceable
- Minimal
- Maintainable

Documentation exists to support implementation—not replace it.

---

# Documentation Roadmap

```
Product
        ↓

Documentation
        ↓

Specifications
        ↓

Implementation
        ↓

Testing
        ↓

Release
```

This hierarchy defines the documentation ecosystem of BizTalkLens.