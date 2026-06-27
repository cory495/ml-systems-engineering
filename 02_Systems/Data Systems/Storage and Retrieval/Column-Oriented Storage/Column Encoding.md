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
# Column Encoding

Date: 2026-06-15

---

## 1. Problem

How do we reduce storage size and improve query performance in column-oriented databases?

Raw column storage is still inefficient without compression-aware encoding.

---

## 2. Intuition

Instead of storing raw values, we store **encoded representations** that exploit patterns in each column.

Why?

Because columns often contain:
- Repeated values
- Sorted or semi-sorted data
- Low cardinality (e.g., country, gender)

---

## 3. How It Works

Common encoding strategies:

- Dictionary encoding → replace values with integer IDs
- Run-length encoding → compress repeated values
- Delta encoding → store differences between values
- Bit-packing → use minimal bits per value

---

## 4. Key Components

- Encoding dictionary
- Value compression layer
- Column chunk storage
- Type-aware encoders

---

## 5. Tradeoffs

### Pros
- Smaller storage footprint
- Faster disk reads
- Better cache utilization

### Cons
- Encoding/decoding overhead
- Complex write pipeline
- Not all data compresses well

---

## 6. Real Systems Usage

- Parquet
- ORC
- ClickHouse
- BigQuery
- Snowflake internal formats

---

## 7. Summary

Column encoding improves storage efficiency by transforming raw column values into compact representations tailored to data distribution.