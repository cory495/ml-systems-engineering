---
Created: 2026-06-01
Updated: 2026-06-26
tags:
  - systems
  - programming
  - databases
  - distributed-systems
Type: Notes
---
# Snowflake Schema

Date: 2026-06-15

---

## 1. Problem

How do we reduce redundancy in dimension tables while still supporting analytical queries?

Star schemas can duplicate dimension data, leading to storage inefficiency.

---

## 2. Intuition

A snowflake schema is a **normalized version of a star schema**.

Instead of one large dimension table, dimensions are split into sub-dimensions.

Think:

> Star schema = flattened dimensions  
> Snowflake schema = normalized dimensions

---

## 3. How It Works

- Step 1: Start with fact table
- Step 2: Normalize dimension tables into multiple related tables
- Step 3: Connect via foreign keys between dimension layers
- Step 4: Query requires more joins

---

## 4. Key Components

- Fact table
- Normalized dimension tables
- Hierarchical relationships (e.g., city → state → country)
- Foreign key chains

---

## 5. Tradeoffs

### Pros
- Reduced data redundancy
- Better data consistency
- More structured dimension modeling

### Cons
- More joins → slower queries
- More complex query logic
- Harder for BI users

---

## 6. Scaling / Complexity

- Query complexity increases with join depth
- Storage usage decreases vs star schema
- Better suited for structured enterprise data

---

## 7. Real Systems Usage

- Enterprise data warehouses
- Large-scale relational OLAP systems
- Systems with strict data governance requirements

---

## 8. Failure Modes

- Too many joins → query slowdown
- Over-normalization → hard-to-use schema
- Poor join optimization → expensive queries

---

## 9. Related Concepts

[[Star Schema]]
[[Fact vs Dimension Tables]]
[[Normalization]]
[[Data Warehousing]]

---

## 10. Summary

A snowflake schema normalizes dimension tables in a star schema to reduce redundancy, at the cost of more complex and slower queries.