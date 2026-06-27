---
Created: 2026-06-27
Updated: 2026-06-27
tags:
  - systems
  - distributed-systems
  - scaling
Type: Notes
---

# Partition Rebalancing

Date: 2026-06-27

---

## 1. Problem

As systems scale, partitions become uneven due to:
- growth in data
- shifting traffic patterns
- node failures or additions

We need a mechanism to redistribute data across nodes while maintaining availability.

---

## 2. Intuition

Rebalancing is “redistributing workload fairness.”

It moves data so that no node is overloaded while others are idle.

Think of it as continuously reshuffling responsibilities across a cluster.

---

## 3. How It Works

1. Detect imbalance (load, storage, QPS)
2. Select partitions to move
3. Copy data to target node
4. Update routing metadata
5. Redirect traffic gradually
6. Remove old partition ownership

Techniques:
- streaming replication during transfer
- dual writes or read-repair during migration

---

## 4. Key Components

- load monitor
- partition assignment manager
- data migration pipeline
- routing metadata system
- consistency controller

---

## 5. Tradeoffs

### Pros
- improves load distribution
- enables horizontal scaling
- reduces hotspots

### Cons
- expensive data movement
- temporary inconsistency risk
- increased system complexity

---

## 6. Scaling / Complexity

Data movement cost:

$$
O(k)
$$

where \(k\) is data in moved partitions.

System-wide cost depends on migration frequency.

---

## 7. Real Systems Usage

- distributed databases (Cassandra, Dynamo-style systems)
- Kubernetes cluster rescheduling
- distributed file systems (HDFS)
- stream processing rebalancing (Kafka partitions)

---

## 8. Failure Modes

- inconsistent reads during migration
- duplicate writes if coordination fails
- network saturation during rebalance
- partial migration leading to split ownership

Mitigations:
- consistent hashing with gradual migration
- throttled data transfer
- versioned ownership metadata
- quorum-based consistency checks

---

## 9. Related Concepts

[[Dynamic Partitioning]]
[[Fixed Partitioning]]
[[Hotspots]]
[[Data Skew]]
[[Metadata Service]]

---

## 10. Interview Questions

- Why is rebalancing necessary in distributed systems?
- How do you migrate data safely between nodes?
- What consistency issues arise during rebalancing?

---

## 11. Summary

Partition rebalancing redistributes data across nodes to maintain even load and storage utilization. It is essential for scalable distributed systems but introduces complexity, migration overhead, and consistency challenges.