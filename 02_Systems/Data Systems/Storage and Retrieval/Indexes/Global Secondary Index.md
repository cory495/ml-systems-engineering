---
Created: 2026-06-27
Updated: 2026-06-27
tags:
  - systems
  - databases
  - indexing
Type: Notes
---

# Global Secondary Index

Date: 2026-06-27

---

## 1. Problem

Local indexes are restricted to a single partition, which makes cross-partition queries inefficient or impossible.

We need a mechanism to query data efficiently **across all partitions using non-primary attributes**.

Global Secondary Index (GSI) solves this by creating a **separate index structure independent of the base partitioning scheme**.

---

## 2. Intuition

A Global Secondary Index is a “parallel database view” optimized for a different query pattern.

Instead of searching each partition, you consult a separate structure designed specifically for the attribute you care about.

Think:
- base table = original dataset layout
- GSI = alternate “lookup map” across the entire dataset

---

## 3. How It Works

1. Base table is partitioned by primary key
2. GSI is maintained as a separate distributed structure
3. Each update to base table is propagated to GSI asynchronously or synchronously
4. Queries on secondary attributes go directly to GSI
5. GSI returns pointers or full records depending on design

---

## 4. Key Components

- base table partitions
- global index table
- replication / propagation pipeline
- consistency mechanism (eventual or strong)
- query routing layer

---

## 5. Tradeoffs

### Pros
- supports queries without knowing partition key
- enables flexible query patterns
- reduces need for scatter/gather reads

### Cons
- higher write amplification
- increased storage overhead
- consistency lag between base and index
- more complex system design

---

## 6. Scaling / Complexity

Write cost:

$$
O(k)
$$

where \(k\) = number of indexes updated per write

Read cost:

$$
O(\log n)
$$

or better depending on index structure.

---

## 7. Real Systems Usage

- DynamoDB Global Secondary Indexes
- Cassandra secondary index implementations (varied)
- search systems (Elasticsearch-style indexing)
- OLAP systems with materialized views

---

## 8. Failure Modes

- index lag causing stale reads
- write amplification bottlenecks
- inconsistent index-base divergence
- hot partitions in index layer

Mitigations:
- asynchronous update pipelines with retry
- backpressure on index writers
- reconciliation jobs
- eventual consistency guarantees

---

## 9. Related Concepts

[[Secondary Index]]
[[Local Secondary Index]]
[[Partitioning]]
[[Write Amplification]]
[[Eventual Consistency]]

---

## 10. Interview Questions

- What is a global secondary index?
- How does it differ from a local secondary index?
- Why does it increase write cost?
- How do systems keep GSIs consistent?

---

## 11. Summary

Global Secondary Indexes provide cross-partition query capability by maintaining a separate distributed index structure. They greatly improve query flexibility but introduce write amplification, consistency challenges, and additional system complexity.