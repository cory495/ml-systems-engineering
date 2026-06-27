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
# Vectorized Execution

Date: 2026-06-15

---

## 1. Problem

How do we efficiently process large analytical queries without per-row interpretation overhead?

Traditional execution processes one row at a time, which is inefficient.

---

## 2. Intuition

Instead of processing rows individually:

> Process data in batches (vectors) of thousands of rows at a time.

This allows CPU-level optimizations like SIMD and cache efficiency.

---

## 3. How It Works

- Step 1: Load column chunks into memory
- Step 2: Process data in batches (vectors)
- Step 3: Apply operations across entire arrays
- Step 4: Output aggregated or filtered results

---

## 4. Key Components

- Vectorized operators
- Batch processing engine
- CPU cache optimization
- Column batches

---

## 5. Tradeoffs

### Pros
- High CPU efficiency
- Better cache locality
- Reduced function call overhead
- Enables SIMD acceleration

### Cons
- More memory usage per batch
- Not ideal for OLTP workloads
- More complex execution engine

---

## 6. Real Systems Usage

- ClickHouse
- DuckDB
- Snowflake
- BigQuery
- Apache Arrow-based systems

---

## 7. Summary

Vectorized execution processes data in batches instead of row-by-row, dramatically improving analytical query performance through CPU and cache optimization.