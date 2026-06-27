---
Created: 2026-06-27
Updated: 2026-06-27
tags:
  - systems
  - distributed-systems
  - fault-tolerance
Type: Concept
---

# Conflict Resolution

Date: 2026-06-27

---

## 1. Problem

In distributed systems, concurrent writes and network partitions can lead to divergent replicas with conflicting updates.

We need a deterministic way to decide which version of data should be considered correct.

---

## 2. Intuition

Conflict resolution is “deciding what wins when there is no global agreement.”

Because systems cannot always coordinate in real time, conflicts are inevitable and must be resolved after the fact.

---

## 3. How It Works

Common strategies:

### 1. Last Write Wins (LWW)
- choose value with highest timestamp

### 2. Version Vectors
- track causality across replicas
- merge non-conflicting updates

### 3. Application-level merge
- user-defined merge functions

### 4. CRDTs
- mathematically mergeable data types

---

## 4. Key Components

- timestamps or logical clocks
- version vectors
- merge functions
- replica metadata

---

## 5. Tradeoffs

### Pros
- enables availability under partitions
- flexible resolution strategies
- supports eventual consistency

### Cons
- potential data loss (LWW)
- complexity (CRDTs, version vectors)
- ambiguous semantics in merges

---

## 6. Scaling / Complexity

LWW resolution:

$$
O(1)
$$

Version vector comparison:

$$
O(N)
$$

CRDT merges:

$$
O(k)
$$

---

## 7. Real Systems Usage

- Dynamo-style systems (LWW)
- Cassandra
- collaborative editing tools (CRDTs)
- distributed caches

---

## 8. Failure Modes

- clock skew causing incorrect ordering
- lost updates under LWW
- merge conflicts in complex structures
- metadata overhead in large clusters

Mitigations:
- logical clocks (Lamport, vector clocks)
- CRDT adoption
- application-aware merge logic

---

## 9. Related Concepts

[[Quorums]]
[[Read Repair]]
[[Anti-Entropy]]
[[Network Partitions]]
[[CAP Theorem]]

---

## 10. Interview Questions

- What is conflict resolution?
- Why is LWW dangerous?
- How do CRDTs avoid conflicts?
- What role do vector clocks play?

---

## 11. Summary

Conflict resolution defines how distributed systems reconcile divergent updates caused by concurrency or partitions, using strategies ranging from simple timestamp ordering to complex CRDT-based merges.