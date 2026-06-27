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
# Star Schema

Date: 2026-06-15

---

## 1. Problem

How do we design schemas that make analytical queries fast and simple?

Normalized schemas require many joins, which slows down OLAP workloads.

---

## 2. Intuition

A star schema organizes data into:

- A central **fact table**
- Surrounding **dimension tables**

Like a star shape:

```
        Dimension
           |
Dimension - Fact - Dimension
           |
        Dimension
```

The goal is to minimize joins during analytical queries.

---

## 3. How It Works

- Step 1: Identify measurable events (facts)
- Step 2: Store them in a central fact table
- Step 3: Attach descriptive context in dimension tables
- Step 4: Query via joins from fact → dimensions

---

## 4. Key Components

- Fact table (metrics, events, transactions)
- Dimension tables (users, products, time, location)
- Foreign keys
- Denormalized attributes in dimensions

---

## 5. Tradeoffs

### Pros
- Fast analytical queries
- Simple join patterns
- Easy to understand and query
- Optimized for OLAP engines

### Cons
- Data duplication in dimensions
- Less efficient for updates
- Not suitable for OLTP workloads

---

## 6. Scaling / Complexity

- Fact tables can grow extremely large (billions of rows)
- Dimension tables remain relatively small
- Query cost depends on fact table scans

---

## 7. Real Systems Usage

- Snowflake (typical modeling pattern)
- BigQuery data warehouses
- Redshift schemas
- Business intelligence dashboards (Tableau, Looker)

---

## 8. Failure Modes

- Huge fact tables without partitioning → slow scans
- Poor dimension design → redundant joins
- Missing indexes → full table scans

---

## 9. Related Concepts

[[Fact vs Dimension Tables]]
[[Snowflake Schema]]
[[Data Warehousing]]
[[Column-Oriented Storage]]

---

## 10. Summary

A star schema structures analytical data around a central fact table and surrounding dimension tables, minimizing joins and optimizing query performance.