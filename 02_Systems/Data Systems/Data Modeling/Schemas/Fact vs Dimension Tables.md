---
Created: 2026-06-01
Updated: 2026-06-26
tags:
  - systems
  - programming
  - databases
Type: Notes
---
# Fact vs Dimension Tables

Date: 2026-06-15

---

## 1. Problem

How do we structure analytical data so that metrics and context are cleanly separated?

Mixing raw events and descriptive data leads to inefficient and confusing schemas.

---

## 2. Intuition

Data in OLAP systems is split into:

- **Facts** → measurable events (what happened)
- **Dimensions** → descriptive context (who, what, where, when)

Think:

> Fact = numbers  
> Dimension = explanation of numbers

---

## 3. How It Works

### Fact tables
- Store events or transactions
- Usually numeric and additive
- High volume

Examples:
- sales amount
- clicks
- transactions
- page views

---

### Dimension tables
- Provide context
- Low volume compared to facts
- Descriptive attributes

Examples:
- user info
- product details
- time/date
- location

---

## 4. Key Components

- Fact table (metrics, foreign keys)
- Dimension tables (attributes)
- Surrogate keys
- Foreign key relationships

---

## 5. Tradeoffs

### Pros
- Clear separation of concerns
- Efficient OLAP querying
- Scalable schema design

### Cons
- Requires joins
- More complex modeling
- Risk of inconsistent dimensions

---

## 6. Scaling / Complexity

- Fact tables scale to billions of rows
- Dimension tables remain small
- Query cost dominated by fact table scans

---

## 7. Real Systems Usage

- BigQuery analytics models
- Snowflake data models
- Redshift BI schemas
- Star and snowflake schemas

---

## 8. Failure Modes

- Fact table explosion (unbounded growth)
- Dimension mismatch (broken joins)
- Poor key design → slow joins

---

## 9. Related Concepts

[[Star Schema]]
[[Snowflake Schema]]
[[Data Warehousing]]
[[Schema Design]]

---

## 10. Summary

Fact tables store measurable events, while dimension tables store descriptive context. This separation is fundamental to OLAP and data warehouse design.