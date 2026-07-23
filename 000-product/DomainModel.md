# BizTalkLens Domain Model

Version: 1.0

---

# 1. Purpose

This document defines the conceptual business model of BizTalkLens.

It establishes the domain objects, their responsibilities, their relationships, and the business rules that govern them.

The Domain Model is technology-independent.

It does not define:

- Database schemas
- REST APIs
- JSON models
- Entity Framework entities
- C# classes
- Project structure

Those concerns belong to the implementation specifications.

The purpose of the Domain Model is to answer one question:

> **What business concepts exist inside BizTalkLens?**

---

# 2. Domain Philosophy

BizTalkLens is fundamentally an Enterprise Integration Knowledge Platform.

Its domain revolves around transforming technical evidence into enterprise knowledge.

The domain follows a deterministic progression.

```

Workspace
↓
Discovery Session
↓
Evidence
↓
Knowledge
↓
Graph
↓
Analysis
↓
Finding
↓
Recommendation
↓
Documentation
↓
Report

```

Each concept represents a distinct business responsibility.

No concept duplicates another.

---

# 3. Core Domain Concepts

The platform is built around ten primary domain concepts.

```

Workspace

Discovery Session

Evidence

Knowledge

Graph

Analysis

Finding

Recommendation

Documentation

Report

```

These concepts form the backbone of every business workflow.

---

# 4. Workspace

## Definition

A Workspace represents a customer engagement.

It is the highest-level business entity within BizTalkLens.

Everything belongs to exactly one Workspace.

---

## Responsibilities

A Workspace is responsible for:

- Managing discovery sessions
- Organizing evidence
- Maintaining knowledge
- Holding findings
- Holding recommendations
- Storing generated reports
- Managing configuration

---

## Owns

- Discovery Sessions
- Evidence
- Knowledge Model
- Findings
- Recommendations
- Reports
- Documents

---

## Business Rules

A Workspace:

- has one owner
- may contain many discovery sessions
- may contain many environments
- maintains historical execution history
- is isolated from other workspaces

---

# 5. Discovery Session

## Definition

A Discovery Session represents one execution of the discovery process.

It captures the complete state of an environment at a specific point in time.

---

## Responsibilities

A Discovery Session:

- coordinates providers
- records execution metadata
- produces evidence
- records execution duration
- records provider versions
- records failures
- records warnings

---

## Business Rules

A Discovery Session:

belongs to one Workspace

contains many Evidence records

never modifies previous sessions

is immutable after completion

---

# 6. Evidence

## Definition

Evidence is an immutable observation collected from a source system.

Evidence is factual.

It contains no interpretation.

---

## Responsibilities

Evidence records:

what was observed

where it came from

when it was observed

which provider discovered it

---

## Examples

BizTalk Application

Pipeline

Schema

Map

Host

Certificate

SQL Database

Receive Location

Send Port

API Endpoint

---

## Business Rules

Evidence:

is immutable

belongs to one Discovery Session

has one origin

may contribute to multiple Knowledge objects

never references Recommendations

---

# 7. Knowledge

## Definition

Knowledge represents interpreted information created from Evidence.

Knowledge establishes relationships.

Knowledge introduces meaning.

---

## Responsibilities

Knowledge determines:

ownership

dependencies

technology

relationships

business context

integration context

---

## Examples

Application A owns Interface X.

Schema Y is shared.

System Z communicates with SAP.

Pipeline P validates XML.

---

## Business Rules

Knowledge:

references one or more Evidence records

is versioned

is searchable

is technology-neutral

never invents unsupported facts

---

# 8. Graph

## Definition

The Graph is the navigable representation of the Knowledge Model.

It enables traversal, dependency analysis, visualization, and impact assessment.

---

## Node Types

Application

Artifact

Interface

Server

Database

Environment

Technology

Protocol

External System

Certificate

Queue

API

---

## Relationship Types

Contains

Uses

Depends On

Calls

References

Transforms

Hosts

Consumes

Produces

Communicates With

Owns

Deploys

---

## Business Rules

Every Graph node represents a Knowledge entity.

Every Graph relationship represents a Knowledge relationship.

No Graph element exists independently of Knowledge.

---

# 9. Analysis

## Definition

Analysis evaluates the Knowledge Model.

It identifies patterns and produces Findings.

---

## Responsibilities

Analysis measures:

complexity

risk

dependencies

technology usage

reuse

migration readiness

operational concerns

---

## Business Rules

Analysis:

never changes Knowledge

never changes Evidence

produces Findings

is deterministic

---

# 10. Finding

## Definition

A Finding is an evidence-backed observation.

It represents something noteworthy about the environment.

---

## Examples

High complexity

Unsupported adapter

Circular dependency

Missing documentation

High coupling

Legacy protocol

Shared schema

Custom pipeline component

---

## Business Rules

A Finding:

belongs to one Analysis execution

references one or more Knowledge objects

references supporting Evidence

may generate Recommendations

---

# 11. Recommendation

## Definition

A Recommendation is actionable engineering guidance.

Recommendations are produced from Findings.

---

## Responsibilities

Recommendations describe:

what should change

why it should change

expected effort

risk

benefits

limitations

alternatives

---

## Business Rules

Every Recommendation:

references Findings

references Evidence

contains confidence

contains rationale

is platform specific

---

# 12. Documentation

## Definition

Documentation is structured technical knowledge generated from the Knowledge Model.

---

## Examples

Application Guide

Interface Guide

Environment Guide

Infrastructure Guide

Integration Guide

Technology Inventory

Dependency Documentation

---

## Business Rules

Documentation:

is reproducible

is versioned

references Knowledge

does not introduce new information

---

# 13. Report

## Definition

A Report presents information for a specific audience.

---

## Report Types

Executive

Technical

Operational

Architecture

Migration

Risk

Infrastructure

Technology

---

## Business Rules

Reports:

are generated

never manually maintained

reference Knowledge

reference Findings

reference Recommendations

---

# 14. Aggregate Boundaries

The domain is organized into aggregates.

```

Workspace
└── Discovery Sessions

Discovery Session
└── Evidence

Knowledge
├── Graph
├── Analysis
├── Findings
└── Recommendations

Documentation

Reports

```

Each aggregate protects its own consistency.

Communication between aggregates occurs through well-defined application services.

---

# 15. Domain Relationships

```

Workspace
│
├── Discovery Sessions
│
├── Evidence
│
└── Knowledge
│
├── Graph
│
├── Analysis
│
│
├── Findings
│
└── Recommendations
│
├── Documentation
│
└── Reports

```

---

# 16. Domain Rules

The following rules govern the entire domain.

## Rule 1

Evidence is immutable.

---

## Rule 2

Knowledge is derived only from Evidence.

---

## Rule 3

Graphs are derived only from Knowledge.

---

## Rule 4

Analysis consumes Knowledge.

---

## Rule 5

Findings are produced only by Analysis.

---

## Rule 6

Recommendations are produced only from Findings.

---

## Rule 7

Reports never bypass the Knowledge Model.

---

## Rule 8

Documentation is generated.

It is never manually authored inside BizTalkLens.

---

## Rule 9

Every business object is traceable to Evidence.

---

## Rule 10

Every Recommendation is explainable.

---

# 17. Domain Lifecycle

```

Workspace

↓

Discovery Session

↓

Evidence

↓

Knowledge

↓

Graph

↓

Analysis

↓

Finding

↓

Recommendation

↓

Documentation

↓

Report

```

This lifecycle defines the fundamental business process of BizTalkLens.

Every implementation, API, service, workflow, and feature shall conform to this lifecycle.

---

# Closing Statement

The Domain Model defines the ubiquitous language of BizTalkLens.

It provides a technology-independent description of the platform's business concepts and their relationships.

All implementation specifications, source code, tests, APIs, and documentation shall align with this model to ensure architectural consistency, traceability, and long-term maintainability.