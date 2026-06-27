---
Created: 2026-06-27
Updated: 2026-06-27
tags:
  - systems
  - distributed-systems
  - partitioning
Type: Notes
---

# Key Range Partitioning

Date: 2026-06-27

---

## 1. Problem

We need a way to distribute ordered data across multiple nodes while preserving query efficiency for range-based access.

Without range partitioning, queries like “all keys between A and B” require scanning many shards.

---

## 2. Intuition

Key range partitioning keeps **sorted keys together on the same node**.

Each node owns a continuous interval of the keyspace.

Think of it like slicing a sorted list into contiguous chunks.

---

## 3. How It Works

1. Define key ordering (lexicographic or numeric)
2. Split keyspace into contiguous ranges
3. Assign each range to a node
4. Route requests based on key interval

When load changes:
- ranges may be split or merged

---

## 4. Key Components

- ordered keyspace
- range boundaries
- routing table
- partition manager

---

## 5. Tradeoffs

### Pros
- efficient range queries
- locality for sequential access
- good for time-series data

### Cons
- hotspot risk (sequential key growth)
- uneven distribution under skew
- expensive rebalancing

---

## 6. Scaling / Complexity

Lookup:

$$
O(\log n)
$$

Range scan:

$$
O(k + \log n)
$$

where \(k\) is number of results.

---

## 7. Real Systems Usage

- Bigtable / HBase row-key ranges
- time-series databases
- log storage systems
- OLAP systems with sorted keys

---

## 8. Failure Modes

- hotspots from monotonically increasing keys (e.g., timestamps)
- uneven range sizes
- expensive split operations during scaling

Mitigations:
- pre-splitting ranges
- salting keys
- dynamic rebalancing

---

## 9. Related Concepts

[[Hash Partitioning]]
[[Consistent Hashing]]
[[Composite Keys]]
[[Partition Rebalancing]]
[[Data Skew]]

---

## 10. Interview Questions

- Why is range partitioning good for time-series data?
- What causes hotspots in range partitioning?
- How do systems split and merge ranges?

---

## 11. Summary

Key range partitioning distributes data using ordered key intervals, enabling efficient range queries but risking hotspots when keys are not uniformly distributed.