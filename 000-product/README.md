# Product

The **Product** directory defines the business foundation of BizTalkLens.

These documents explain **why BizTalkLens exists**, **what it is intended to accomplish**, and **the business concepts that define the platform**.

The Product documentation is the highest level of documentation within the repository.

Every architectural decision, engineering specification, implementation, and test should ultimately trace back to the product vision documented here.

---

# Purpose

The purpose of this directory is to establish a common understanding of BizTalkLens before discussing architecture or implementation.

The documents contained here describe:

- Product Vision
- Product Scope
- Product Philosophy
- Business Terminology
- Product Architecture
- Domain Model

These documents are intentionally technology independent.

They describe the product rather than its implementation.

---

# Document Hierarchy

| Document | Purpose |
|----------|---------|
| Vision.md | Defines why BizTalkLens exists and its long-term vision |
| Glossary.md | Defines the ubiquitous language used throughout the repository |
| Architecture.md | Defines the conceptual architecture of the platform |
| DomainModel.md | Defines the business domain and its core concepts |

---

# Relationship to Other Directories

```
Product
     │
     ▼
Engineering Documentation
     │
     ▼
Implementation Specifications
     │
     ▼
Source Code
     │
     ▼
Tests
```

The Product directory should remain stable over time.

Engineering details belong elsewhere.

---

# Guiding Principle

The Product documentation answers four questions:

**Why does the product exist?**

**What problem does it solve?**

**How is the product conceptually organized?**

**Which business concepts define the platform?**

Implementation decisions should never contradict these documents.