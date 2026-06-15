# Materialized Views

Date: 2026-06-15

---

## 1. Problem

How do we speed up expensive queries without recomputing them from scratch every time?

Repeated aggregation queries are expensive in large datasets.

---

## 2. Intuition

A materialized view is a **precomputed query result stored as a table**.

Instead of recalculating:

```SQL
SELECT region, SUM(sales)
FROM sales
GROUP BY region
```

we store the result and update it periodically or incrementally.

Think:

> “Cache the result of a query, not just the data.”

---

## 3. How It Works

- Step 1: Define a query as a view
- Step 2: Execute query once and store result
- Step 3: Refresh view periodically or incrementally
- Step 4: Query engine uses stored result instead of base tables

---

## 4. Key Components

- Base tables
- View definition (SQL query)
- Stored result table
- Refresh strategy (batch or incremental)

---

## 5. Tradeoffs

### Pros
- Fast query performance
- Reduces compute cost
- Useful for dashboards and reporting

### Cons
- Stale data risk
- Storage overhead
- Maintenance complexity
- Expensive refresh operations

---

## 6. Real Systems Usage

- PostgreSQL materialized views
- Snowflake result caching + materialized views
- BigQuery materialized views
- Redshift aggregate tables

---

## 7. Failure Modes

- Outdated results due to delayed refresh
- Expensive full recomputation
- Inconsistent state with base tables
- Query planner not selecting view

---

## 8. Related Concepts

[[Data Cubes]]
[[OLAP]]
[[Data Warehousing]]
[[Column-Oriented Storage]]
[[Batch Processing]]

---

## 9. Summary

Materialized views store precomputed query results to accelerate repeated analytical queries, trading storage and freshness for performance.