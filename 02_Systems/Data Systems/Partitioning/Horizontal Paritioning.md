---
Created: 2026-06-27
Updated: 2026-06-27
tags:
  - systems
  - distributed-systems
  - partitioning
Type: Notes
---

# Horizontal Partitioning

Date: 2026-06-27

---

## 1. Problem

As datasets grow, storing all rows in a single database becomes a bottleneck for performance and scalability.

We need a way to distribute rows across multiple machines while preserving the same schema.

---

## 2. Intuition

Horizontal partitioning splits a table **by rows**, not columns.

Each partition contains a subset of records, but all partitions share the same schema.

Think: “splitting a spreadsheet into multiple smaller spreadsheets, each with full columns but fewer rows.”

---

## 3. How It Works

1. Choose partition key (e.g., user_id)
2. Apply partitioning function:
   - hash-based
   - range-based
3. Assign rows to partitions
4. Route queries based on partition key
5. Aggregate results if needed across partitions

---

## 4. Key Components

- partition key
- routing layer
- shard nodes
- partition map
- query coordinator

---

## 5. Tradeoffs

### Pros
- scales write and storage capacity
- enables parallel query execution
- isolates failures per shard

### Cons
- cross-shard queries are expensive
- hotspot risk with poor keys
- rebalancing complexity

---

## 6. Scaling / Complexity

Lookup:

$$
O(1)
$$

Cross-partition query:

$$
O(n)
$$

where \(n\) is number of shards.

---

## 7. Real Systems Usage

- distributed SQL databases
- NoSQL systems (Cassandra, DynamoDB)
- microservice data stores
- multi-tenant systems

---

## 8. Failure Modes

- skewed partition keys causing hotspots
- uneven shard sizes
- expensive resharding operations
- inconsistent query performance across shards

Mitigations:
- consistent hashing
- composite keys
- dynamic partitioning
- caching layers

---

## 9. Related Concepts

[[Partitioning]]
[[Vertical Partitioning]]
[[Sharding]]
[[Hotspots]]
[[Data Skew]]

---

## 10. Interview Questions

- What is horizontal partitioning?
- How does it differ from vertical partitioning?
- What problems arise with poor partition keys?

---

## 11. Summary

Horizontal partitioning splits a dataset by rows across multiple machines, enabling horizontal scalability while maintaining a consistent schema across partitions.