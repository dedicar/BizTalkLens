# Engineering Principles

Version: 1.0
Status: Approved

---

# Purpose

These principles govern all engineering decisions within BizTalkLens.

Whenever implementation choices conflict with these principles, these principles take precedence.

---

# Principle 1 — Product First

Architecture is organized around product responsibilities.

Never around frameworks.

---

# Principle 2 — Behavior First

BDD defines expected behavior before implementation begins.

Features are described in terms of observable outcomes.

---

# Principle 3 — Domain Driven

DDD models the engineering concepts of BizTalkLens.

Examples include:

- Discovery Session
- Evidence
- Knowledge Graph
- Artifact
- Relationship

---

# Principle 4 — Clean Modules

Clean Architecture is applied inside modules.

Projects are not organized into Domain/Application/Infrastructure.

Modules are.

---

# Principle 5 — Immutable Dependencies

Dependencies always flow in one direction.

No cyclic references.

---

# Principle 6 — Thin Hosts

CLI

API

Web

are delivery mechanisms only.

Business logic belongs inside Engine.

---

# Principle 7 — Composition Root

Hosting is the only Composition Root.

Dependency Injection shall be configured only here.

---

# Principle 8 — Technology Independence

The Engine shall remain independent of:

- Databases
- UI frameworks
- ExplorerOM
- WMI
- SQL
- Azure
- PowerShell

Technology changes.

The domain should not.

---

# Principle 9 — Extensibility

Every Connector should be independently deployable.

Every Extension should be independently deployable.

Adding new capabilities should require minimal modification to existing code.

---

# Principle 10 — Modularity

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

Modules should be cohesive and loosely coupled.

---

# Principle 11 — Testability

The Engine shall be executable without:

- Console
- API
- UI
- SQL
- ExplorerOM

Business logic must be testable in isolation.

---

# Principle 12 — Explicitness

Prefer explicit behavior over implicit magic.

Avoid hidden dependencies.

Avoid reflection unless necessary for extensibility.

Avoid service locators.

---

# Principle 13 — Immutability

Prefer immutable models.

Prefer value objects.

Minimize mutable shared state.

---

# Principle 14 — Simplicity

Prefer the simplest architecture capable of solving the problem.

Avoid premature abstraction.

Avoid speculative generalization.

---

# Principle 15 — Long-Term Stability

Solution projects represent long-lived architectural boundaries.

Implementation patterns may evolve.

Product responsibilities should remain stable.