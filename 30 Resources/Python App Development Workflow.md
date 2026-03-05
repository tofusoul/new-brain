---
Type: Resource
tags: [resource, python, development, workflow]
---

# Python App Development Workflow

**Type:** Personal Development Methodology

## Overview
Preferred approach for building Python applications with focus on data understanding, functional programming patterns, and rapid prototyping.

## Development Process

### 1. Understand Source Data
**Goal:** Collect and understand data before development

**Steps:**
- Collect data into a data lake
- Parse and persist data into Parquet files
  - Handles basic typing problems automatically
  - Efficient storage and fast access

### 2. Shape and Model Data
**Tool:** Pandas (as swiss army knife)

**Approach:**
- Use Pandas for data manipulation and shaping
- Model data with **frozen dataclasses**
  - Enables functional programming interactions
  - Type safety and immutability
  - Clear data contracts

### 3. Mock UI and Interactions
**Tool:** Streamlit

**Benefits:**
- Rapid prototyping without frontend development
- Interactive data exploration
- Quick user feedback loops

### 4. Persist Data
**Tool:** DuckDB

**Integration:**
- Map dataclass models to database schema
- In-process SQL database
- Excellent performance for analytical queries
- Parquet integration

## Technology Stack

| Component | Tool | Purpose |
|-----------|------|---------|
| Data Storage | Parquet files | Efficient columnar storage |
| Data Shaping | Pandas | Data manipulation and analysis |
| Data Modeling | Frozen dataclasses | Type-safe, immutable models |
| UI Prototyping | Streamlit | Rapid web-based UI |
| Database | DuckDB | In-process SQL analytics |

## Related Resources
- [[Pandas]] - Data manipulation library
- [[DuckDB]] - Analytical database
- [[Pydantic]] - Data validation alternative
- [[Streamlit]] - UI framework
- [[Python]] - Programming language
- [[Dataclasses]] - Python data modeling

---
*Last updated: 2025-02-01*
