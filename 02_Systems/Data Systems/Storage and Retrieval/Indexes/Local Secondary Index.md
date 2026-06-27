---
Created: 2026-06-27
Updated: 2026-06-27
tags:
  - systems
  - databases
  - indexing
  - distributed-systems
Type: Notes
---

# Local Secondary Index

Date: 2026-06-27

---

## 1. Problem

Primary-key-based partitioning systems are efficient for direct lookups but inefficient when queries require filtering on non-primary attributes.

We need a way to support secondary queries without scanning entire datasets.

Local Secondary Index (LSI) solves this by keeping the index **within the same partition as the base data**.

---

## 2. Intuition

A Local Secondary Index is a “side dictionary” for a single partition.

It does not change where data lives. Instead, it reorganizes how you search inside one partition.

Think:
- partition = bookshelf
- LSI = index card catalog for that bookshelf only

---

## 3. How It Works

1. Data is partitioned by primary key
2. Within each partition, additional indexes are maintained on alternate attributes
3. Queries on secondary attributes are routed to the correct partition
4. The local index is used to locate matching records inside that partition

Key constraint:
- Index scope is limited to a single partition

---

## 4. Key Components

- partition key (primary sharding key)
- local index structure (B-tree / hash / sorted map)
- base table storage
- query routing layer

---

## 5. Tradeoffs

### Pros
- strong locality (fast within partition)
- no cross-partition coordination required
- simpler consistency model than global indexes

### Cons
- cannot query across partitions efficiently
- requires knowing partition key for routing
- uneven index usefulness if data is skewed

---

## 6. Scaling / Complexity

Lookup within partition:

$$
O(\log n)
$$

But only within a single shard.

System limitation:
- queries without partition key degrade to scatter/gather-like behavior

---

## 7. Real Systems Usage

- DynamoDB local secondary indexes
- Cassandra clustering columns (similar concept)
- partition-local search optimizations
- time-series databases with partitioned time windows

---

## 8. Failure Modes

- uneven partition index growth
- hotspots if certain partitions dominate queries
- stale index entries after updates
- poor performance when queries are not partition-key aware

Mitigations:
- careful partition key design
- TTL-based cleanup
- compaction strategies

---

## 9. Related Concepts

[[Secondary Index]]
[[Global Secondary Index]]
[[Partitioning]]
[[Scatter/Gather Queries]]
[[Metadata Service]]

---

## 10. Interview Questions

- What is a local secondary index?
- Why is it limited to a single partition?
- What are the tradeoffs vs global secondary indexes?
- When would you choose LSI over GSI?

---

## 11. Summary

Local Secondary Indexes provide efficient querying within a single partition by maintaining auxiliary index structures co-located with the base data. They are fast and simple but limited by partition boundaries, making them unsuitable for cross-partition queries.