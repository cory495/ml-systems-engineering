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
# OLTP vs OLAP

Date: 2026-06-15

---

## 1. Problem

Why do we need two fundamentally different types of database systems?

Because transactional workloads and analytical workloads have opposite requirements.

---

## 2. Intuition

- OLTP = fast, precise, real-time operations (business execution)
- OLAP = large-scale analysis (business understanding)

They optimize for different axes:

> OLTP → low-latency writes + point reads  
> OLAP → high-throughput reads + aggregations

---

## 3. How It Works

### OLTP systems
- Many small transactions
- Point lookups and updates
- Highly normalized schema
- Strong consistency

### OLAP systems
- Large scans over datasets
- Aggregations (SUM, AVG, GROUP BY)
- Denormalized or star schemas
- Batch or columnar execution

---

## 4. Key Differences

| Dimension | OLTP | OLAP |
|----------|------|------|
| Workload | Transactions | Analytics |
| Query type | Point queries | Aggregations |
| Data model | Normalized | Denormalized |
| Storage | Row-oriented | Column-oriented |
| Latency | Low (ms) | Higher (seconds-minutes) |

---

## 5. Tradeoffs

### OLTP
- Pros: fast writes, consistency, real-time updates
- Cons: poor for analytics

### OLAP
- Pros: fast analytics, scalable scans
- Cons: slow ingestion, higher latency

---

## 6. Real Systems Usage

- OLTP: PostgreSQL, MySQL, SQLite
- OLAP: BigQuery, Snowflake, Redshift

---

## 7. Failure Modes

- Using OLTP for analytics → slow queries
- Using OLAP for transactions → poor latency
- Mixing workloads → resource contention

---

## 8. Related Concepts

[[Data Warehousing]]
[[Column-Oriented Storage]]
[[Schema Design]]
[[Batch Processing]]
[[OLTP]]
[[OLAP]]

---

## 9. Summary

OLTP systems optimize for transactional workloads, while OLAP systems optimize for analytical workloads. Modern architectures separate the two to avoid conflicting performance goals.