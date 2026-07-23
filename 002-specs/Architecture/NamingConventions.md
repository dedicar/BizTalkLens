# Naming Conventions

Version: 1.0
Status: Approved

---

# Purpose

This document defines naming conventions used throughout BizTalkLens.

Naming shall prioritize:

- Consistency
- Discoverability
- Readability
- Product language

---

# Solution

```
BizTalkLens.sln
```

---

# Projects

Projects represent product responsibilities.

Examples

```
BizTalkLens.Engine

BizTalkLens.Connectors

BizTalkLens.Extensions

BizTalkLens.Hosting

BizTalkLens.Cli

BizTalkLens.Api

BizTalkLens.Web
```

Projects SHALL use PascalCase.

---

# Modules

Modules represent business capabilities.

Examples

```
Discovery

Knowledge

Analysis

Documentation

Reporting

Recommendation
```

Avoid technical names such as:

```
Common

Helpers

Utilities

Manager

Processor

ServiceLayer

InfrastructureLayer
```

---

# Connectors

Connector names describe the external technology.

Examples

```
ExplorerOmConnector

SqlConnector

BizTalk360Connector

PowerShellConnector

WmiConnector

AzureConnector
```

---

# Extensions

Extension names describe the produced value.

Examples

```
PdfExporter

WordExporter

MermaidExporter

ArchitectureReporter

MigrationAdvisor

PlantUmlGenerator
```

---

# Interfaces

Interfaces SHALL begin with I.

Examples

```
IConnector

IExtension

IAnalyzer

ICollector
```

---

# Classes

Classes SHALL be nouns.

Examples

```
DiscoverySession

Evidence

Artifact

KnowledgeGraph

Relationship

Endpoint
```

Avoid suffixes such as:

```
Manager

Helper

Utils

Common

BaseManager
```

---

# Methods

Methods SHALL be verbs.

Examples

```
Collect()

Analyze()

Discover()

Generate()

Correlate()

Export()
```

---

# Properties

Properties SHALL be nouns.

Examples

```
ApplicationName

ServerName

Artifacts

Relationships

Evidence
```

---

# Async Methods

Async methods SHALL end with Async.

```
CollectAsync()

AnalyzeAsync()

ExportAsync()
```

---

# Files

One public type per file.

Filename SHALL match the public type.

---

# Namespaces

Namespaces SHALL mirror folder structure.

---

# Abbreviations

Avoid unnecessary abbreviations.

Prefer

```
Recommendation
```

Instead of

```
Reco
```

Prefer

```
Configuration
```

Instead of

```
Config
```

---

# Product Language

Use the ubiquitous language of BizTalk.

Examples

```
Application

Host

Host Instance

Receive Port

Send Port

Orchestration

Pipeline

Artifact

Knowledge Graph

Evidence

Discovery Session
```

Avoid inventing synonyms.

Consistency is more valuable than creativity.