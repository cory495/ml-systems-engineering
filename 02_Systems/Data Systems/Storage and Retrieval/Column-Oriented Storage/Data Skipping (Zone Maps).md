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
# Data Skipping (Zone Maps)

Date: 2026-06-15

---

## 1. Problem

How do we avoid scanning unnecessary data in large columnar datasets?

Even compressed column stores can still be too large to scan fully.

---

## 2. Intuition

We store **summary metadata per block** so we can skip irrelevant chunks entirely.

Think:

> “Don’t read data that cannot possibly match the query.”

---

## 3. How It Works

- Step 1: Divide data into blocks
- Step 2: For each block, store metadata:
  - min value
  - max value
  - sometimes bloom filters
- Step 3: During query execution:
  - Check metadata first
  - Skip blocks that cannot match predicate

---

## 4. Key Components

- Zone maps (min/max stats)
- Block metadata
- Predicate evaluation layer
- Storage segments

---

## 5. Tradeoffs

### Pros
- Massive query speedup
- Reduces I/O significantly
- Works well with sorted data

### Cons
- Extra metadata storage
- Less effective on unsorted data
- Overhead during writes

---

## 6. Real Systems Usage

- ClickHouse
- Snowflake micro-partitions
- Parquet statistics
- Databricks Delta Lake

---

## 7. Summary

Data skipping uses block-level metadata to avoid reading irrelevant data, significantly reducing I/O in analytical query engines.