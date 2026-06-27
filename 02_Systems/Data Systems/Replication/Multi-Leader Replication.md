---
Created: 2026-06-27
Updated: 2026-06-27
tags:
  - systems
  - distributed-systems
  - replication
Type: Concept
---

# Multi-Leader Replication

Date: 2026-06-27

---

## 1. Problem

Single-leader systems struggle with global latency and availability constraints.

We need a model that allows multiple nodes to accept writes concurrently.

---

## 2. Intuition

Multi-leader replication is “multiple authorities writing in parallel.”

Each region or node can accept writes, which are later synchronized across leaders.

---

## 3. How It Works

1. Multiple leaders accept writes
2. Each leader replicates its changes to others
3. Conflicts may arise due to concurrent updates
4. Conflict resolution strategies reconcile state

---

## 4. Key Components

- multiple leader nodes
- cross-region replication
- conflict resolution mechanism
- versioning system
- anti-entropy synchronization

---

## 5. Tradeoffs

### Pros
- low write latency globally
- high availability
- region-local writes

### Cons
- conflict resolution complexity
- risk of divergence
- harder reasoning about correctness

---

## 6. Scaling / Complexity

Write scalability improves:

$$
O(n_{regions})
$$

but coordination complexity increases:

$$
O(n^2)
$$

---

## 7. Real Systems Usage

- multi-region databases
- collaborative editing systems
- DNS systems
- distributed caching systems

---

## 8. Failure Modes

- write conflicts across regions
- inconsistent resolution strategies
- replication loops
- stale convergence

Mitigations:
- CRDTs
- version vectors
- last-write-wins policies
- anti-entropy protocols

---

## 9. Related Concepts

[[Leader-Based Replication]]
[[Leaderless Replication]]
[[Conflict Resolution]]
[[Replication Lag]]
[[Eventual Consistency]]

---

## 10. Interview Questions

- What is multi-leader replication?
- Why is it useful in multi-region systems?
- How are conflicts resolved?
- What are its failure modes?

---

## 11. Summary

Multi-leader replication allows multiple nodes to accept writes concurrently, improving availability and latency in distributed systems but introducing significant conflict resolution complexity.