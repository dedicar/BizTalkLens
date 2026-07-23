# BizTalkLens Glossary

Version: 1.0

---

# Purpose

This glossary defines the standard terminology used throughout the BizTalkLens repository.

Its objectives are to:

- Establish a shared vocabulary across the product.
- Eliminate ambiguity between business and technical concepts.
- Ensure consistency across documentation, specifications, implementation, and reports.
- Serve as the authoritative reference for terminology used by architects, developers, testers, technical writers, and AI-assisted development tools.

Every specification, design document, source code project, and report should use these definitions consistently.

---

# Core Principles

A term should have exactly one meaning within BizTalkLens.

If two concepts require different meanings, they shall use different names.

Terminology should describe the business domain rather than implementation details.

---

# A

## Adapter

A technology-specific communication component that enables BizTalk Server to exchange messages with external systems.

Examples include FILE, FTP, SFTP, HTTP, WCF, SQL, SAP, Oracle, IBM MQ, and SMTP adapters.

---

## Analysis

The process of evaluating the Knowledge Model to identify patterns, risks, complexity, dependencies, technical debt, modernization readiness, and other insights.

Analysis never modifies the Knowledge Model. It produces Findings.

---

## Analysis Engine

A subsystem responsible for executing one or more Analysis Providers against the Knowledge Model to produce Findings.

---

## Analysis Provider

A pluggable component that performs a specific type of analysis, such as Dependency Analysis, Complexity Analysis, or Risk Analysis.

---

## Application

A logical business solution deployed within BizTalk Server.

An Application groups related artifacts and represents a deployable unit.

---

## Artifact

Any discoverable technical object within an integration environment.

Examples include:

- Schema
- Map
- Pipeline
- Orchestration
- Receive Port
- Send Port
- Assembly
- Business Rule
- Certificate
- SQL Database

Artifacts are discovered during Discovery and represented in the Knowledge Model.

---

# B

## Binding

The configuration that defines runtime settings for BizTalk artifacts, including ports, hosts, adapters, and endpoints.

---

## Business Capability

A business function supported by one or more integration solutions.

Examples include:

- Order Processing
- Customer Management
- Billing
- Inventory Management

Business Capabilities provide business context for technical assets.

---

## Business Rule

A declarative rule executed by the Business Rules Engine (BRE) to implement business logic independently of orchestration code.

---

# C

## Capability

A high-level functional area of BizTalkLens.

Examples include Discovery, Analysis, Reporting, and Recommendations.

Capabilities define what the platform can do rather than how it is implemented.

---

## Confidence Score

A numerical or categorical measure indicating the reliability of a Recommendation.

Confidence is derived from the completeness and quality of supporting Evidence and Findings.

---

## Custom Component

A user-developed extension to BizTalk Server, such as a custom pipeline component, adapter, or .NET assembly.

Custom Components typically increase modernization complexity.

---

# D

## Dependency

A relationship in which one object relies upon another object for correct operation.

Dependencies may exist between applications, artifacts, databases, servers, protocols, or external systems.

---

## Dependency Graph

A graph representation of relationships between Knowledge objects.

Nodes represent entities.

Edges represent dependencies or interactions.

The Dependency Graph enables impact analysis and visualization.

---

## Discovery

The process of collecting technical information from one or more enterprise integration environments.

Discovery is read-only and non-invasive.

Discovery produces Evidence.

---

## Discovery Provider

A technology-specific component responsible for discovering information from a supported platform.

Examples include BizTalk Server, SQL Server, IIS, Windows Server, or Azure Integration Services.

---

## Discovery Session

A single execution of the Discovery process.

Each Discovery Session produces a timestamped collection of Evidence associated with a Workspace.

---

# E

## Endpoint

A communication address used by an integration component.

Examples include:

- HTTP URL
- SOAP Service
- FTP Directory
- File Share
- SQL Connection
- IBM MQ Queue

---

## Environment

A logical deployment stage, such as Development, Test, QA, UAT, or Production.

---

## Evidence

An immutable record of information discovered from a source system.

Evidence always records:

- Origin
- Discovery Session
- Timestamp
- Source Provider

Evidence is factual and contains no interpretation.

---

## Evidence Store

The persistent repository of all Evidence collected during Discovery.

It serves as the historical record of the customer's environment.

---

# F

## Finding

An observation produced by Analysis.

Findings identify conditions, risks, opportunities, or characteristics within the Knowledge Model.

Findings are evidence-backed and may lead to Recommendations.

---

# G

## Graph

A connected representation of entities and relationships.

BizTalkLens models enterprise integration landscapes as graphs to support dependency analysis, search, visualization, and impact assessment.

---

# I

## Integration

A logical interaction between two or more systems.

An Integration may involve message transformation, routing, orchestration, enrichment, validation, or protocol conversion.

---

## Interface

A defined point of communication between systems.

Interfaces describe the contract between producers and consumers.

---

# K

## Knowledge

Structured understanding derived from Evidence.

Knowledge represents interpreted facts, relationships, ownership, and context.

Knowledge is the foundation for Analysis.

---

## Knowledge Model

The normalized representation of the enterprise integration landscape.

It contains entities, relationships, metadata, and business context derived from Evidence.

---

# M

## Modernization

The process of evolving an existing integration solution toward a target platform or architecture.

BizTalkLens provides guidance for modernization but does not perform migration.

---

## Migration

The technical process of moving workloads from one platform to another.

Migration is outside the scope of BizTalkLens.

---

# P

## Pipeline

A BizTalk component responsible for processing messages during receive or send operations.

Pipelines may validate, decode, encode, or transform messages.

---

## Protocol

The communication mechanism used between systems.

Examples include HTTP, HTTPS, SOAP, REST, FTP, SFTP, FILE, SMTP, IBM MQ, and SQL.

---

## Provider

A plug-in that extends BizTalkLens with technology-specific functionality.

Provider categories include:

- Discovery Providers
- Analysis Providers
- Recommendation Providers
- Report Providers
- Visualization Providers

---

# R

## Recommendation

Evidence-backed engineering guidance produced from Findings.

Recommendations describe modernization strategies, risks, estimated effort, platform compatibility, and alternative approaches.

---

## Recommendation Provider

A pluggable component that generates Recommendations for a specific target platform.

Examples include Azure Integration Services, IBM webMethods, and InterSystems IRIS.

---

## Relationship

A connection between two Knowledge entities.

Relationships describe dependency, ownership, communication, usage, or containment.

---

## Report

A structured presentation of information derived from the Knowledge Model.

Reports may target executive, technical, or operational audiences.

---

# S

## Schema

A definition of the structure of a message.

Schemas describe XML, JSON, or other message formats used by integrations.

---

## Source System

An external system from which Discovery collects information.

Examples include BizTalk Server, SQL Server, Windows Server, IIS, and external APIs.

---

# T

## Target Platform

A supported modernization destination evaluated by Recommendation Providers.

Examples include Azure Integration Services, IBM webMethods, and InterSystems IRIS.

---

## Traceability

The ability to follow any Knowledge object, Finding, Recommendation, or Report back to its supporting Evidence.

Traceability is a fundamental principle of BizTalkLens.

---

# V

## Visualization

A graphical representation of the Knowledge Model.

Examples include dependency graphs, architecture diagrams, integration flows, and topology maps.

---

# W

## Workspace

The top-level container representing a customer engagement.

A Workspace contains:

- Configuration
- Discovery Sessions
- Evidence
- Knowledge Model
- Findings
- Recommendations
- Reports

Every operation within BizTalkLens belongs to a Workspace.

---

# Summary

BizTalkLens uses a common language built on four foundational concepts:

**Evidence** represents facts collected during Discovery.

**Knowledge** organizes those facts into meaningful relationships.

**Findings** are observations produced by Analysis.

**Recommendations** provide evidence-backed guidance derived from Findings.

This progression forms the core intellectual model of BizTalkLens:

```text
Discovery
      │
      ▼
Evidence
      │
      ▼
Knowledge
      │
      ▼
Analysis
      │
      ▼
Findings
      │
      ▼
Recommendations
      │
      ▼
Reports
```

Every feature of BizTalkLens should align with this lifecycle.