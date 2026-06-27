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
# Range Queries

Date: 2026-06-15

---

## 1. Problem

How can we efficiently retrieve all records within a range of keys?

Example:

- Get all users with IDs between 1000 and 5000
- Get logs between timestamps T1 and T2

---

## 2. Intuition

Range queries are about **ordering**, not just lookup.

If data is sorted, we can jump to the start of the range and scan sequentially.

If data is not sorted, we must scan everything.

---

## 3. How It Works

With B+ Trees:

- Step 1: Navigate to first key in range
- Step 2: Move through linked leaf nodes
- Step 3: Stop when upper bound is reached

With SSTables:

- Step 1: Identify relevant files
- Step 2: Merge sorted streams
- Step 3: Filter by range

---

## 4. Key Components

- Sorted keys
- Leaf-level ordering
- Sequential disk access
- Index traversal

---

## 5. Tradeoffs

### Pros

- Efficient for ordered data
- Supports analytics queries
- Works well with time-series data

### Cons

- Poor performance on unordered indexes
- Expensive if data is fragmented

### When NOT to use it

- Unindexed attributes
- Highly random access patterns

---

## 6. Scaling / Complexity

### B+ Tree

O(log n + k)

### Full scan

O(n)

### SSTable merge scan

O(n + k)

---

## 7. Real Systems Usage

- Time-series databases
- Logging systems
- Financial systems
- PostgreSQL range queries
- Cassandra clustering keys

---

## 8. Failure Modes

- Poor index choice → full scans
- Fragmented storage → slow sequential access
- Too many SSTables → merge overhead

---

## 9. Related Concepts

[[B+ Tree]]
[[Indexes]]
[[Page Structure]]
[[SSTable]]
[[LSM Tree]]

---

## 10. Interview Questions

- Why are B+ Trees good for range queries?
- How do LSM trees support range scans?
- What makes range queries expensive?

---

## 11. Summary

Range queries rely on sorted data structures and sequential access patterns, making B+ Trees and SSTables the primary supporting structures in modern databases.