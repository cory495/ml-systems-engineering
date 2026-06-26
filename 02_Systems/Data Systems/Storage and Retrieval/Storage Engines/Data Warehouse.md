---
Created: 2026-06-01
Updated: 2026-06-26
tags:
  - systems
  - programming
  - databases
Type: Notes
---
# Data Warehouse

Date: 2026-06-15
---

## 1. Problem

How do organizations efficiently store and analyze massive amounts of historical data across many systems?

Operational databases (OLTP systems) are optimized for fast inserts and point queries, but they perform poorly for:

- Large aggregations
- Historical analysis
- Cross-table scans
- Business intelligence queries

A separate system is needed for analytics at scale.

---

## 2. Intuition

A data warehouse is a **centralized system optimized for analytical queries**, not transactions.

Instead of modeling data around individual operations (like “place order” or “update user”), we model data around questions like:

- “What were total sales per month?”
- “How does retention vary by cohort?”
- “What regions are growing fastest?”

Think:

> OLTP = running the business  
> OLAP = understanding the business

![[pic_data_warehouse.png]]

---

## 3. How It Works

- Step 1: Data is extracted from OLTP systems (databases, logs, services)
- Step 2: Data is transformed into analytical-friendly formats (cleaned, joined, standardized)
- Step 3: Data is loaded into a centralized warehouse
- Step 4: Queries run over large datasets using columnar scans and aggregations

This is commonly known as **ETL (Extract, Transform, Load)** or modern **ELT**.

---

## 4. Key Components

- Data sources (OLTP databases, logs, event streams)
- ETL / ELT pipelines
- Staging area (raw data storage)
- Data warehouse storage engine
- Query engine (SQL-based analytics)
- BI tools (dashboards, reporting systems)

---

## 5. Tradeoffs

### Pros
- Extremely fast analytical queries
- Unified view of data across systems
- Historical data retention
- Optimized for aggregations and scans

### Cons
- High latency for fresh data ingestion
- Complex pipeline infrastructure
- Expensive storage and compute at scale
- Not suitable for real-time updates

### When NOT to use it
- High-frequency transactional workloads
- Low-latency real-time decision systems
- Simple CRUD applications

---

## 6. Scaling / Complexity

### Query Performance
- Optimized for large sequential scans
- Often uses columnar storage → fewer I/O operations

### Ingestion
- Batch or streaming pipelines
- Latency depends on ETL/ELT design

### Bottlenecks
- Data freshness lag
- Join-heavy transformations
- Storage cost at scale
- Compute cost for large aggregations

---

## 7. Real Systems Usage

- Snowflake
- Google BigQuery
- Amazon Redshift
- Databricks (Lakehouse)
- Apache Hive

Used by:

- Netflix analytics
- Uber metrics pipelines
- Airbnb data platform
- Enterprise BI systems

---

## 8. Failure Modes

- Stale data due to delayed pipelines
- Broken ETL jobs leading to missing data
- Schema drift between systems
- Expensive query overruns (unbounded scans)
- Data duplication across pipelines

---

## 9. Related Concepts

[[OLTP]]
[[OLAP]]
[[Batch Processing]]
[[Stream Processing]]
[[Schema-on-Write]]
[[Schema-on-Read]]
[[Column-Oriented Storage]]

---

## 10. Interview Questions

- What is the difference between OLTP and OLAP?
- Why not use a transactional database for analytics?
- What is ETL vs ELT?
- How do data warehouses scale to petabytes?

---

## 11. Summary

Data warehousing is a system design pattern for centralized analytical storage and querying, optimized for large-scale scans, aggregations, and business intelligence rather than transactional workloads.