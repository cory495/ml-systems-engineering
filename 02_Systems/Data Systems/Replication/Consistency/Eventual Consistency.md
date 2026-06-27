---
Created: 2026-06-27
Updated: 2026-06-27
tags:
  - systems
  - distributed-systems
  - consistency
Type: Notes
---

# Eventual Consistency

Date: 2026-06-27

---

## 1. Problem

Strict consistency models reduce availability and increase latency in distributed systems.

We need a model that allows systems to remain available even during partitions, while still converging over time.

---

## 2. Intuition

Eventual consistency means “all replicas will agree eventually if no new writes occur.”

Immediate consistency is sacrificed in favor of availability and partition tolerance.

---

## 3. How It Works

1. Writes are propagated asynchronously
2. Replicas may temporarily diverge
3. Background processes (anti-entropy, gossip, read repair) reconcile differences
4. Over time, all replicas converge to the same state

---

## 4. Key Components

- replication system
- anti-entropy protocol
- conflict resolution strategy
- read repair mechanisms
- versioning system

---

## 5. Tradeoffs

### Pros
- high availability
- low latency writes
- scalable across regions

### Cons
- stale reads
- complex conflict resolution
- temporary inconsistency

---

## 6. Scaling / Complexity

Convergence time:

$$
O(\text{network delay} + \text{replication frequency})
$$

---

## 7. Real Systems Usage

- DynamoDB (eventual consistency mode)
- Cassandra
- DNS systems
- distributed caching systems

---

## 8. Failure Modes

- long-lived divergence under partition
- conflicting updates
- inconsistent reads under high churn
- delayed convergence in low-traffic systems

Mitigations:
- read repair
- anti-entropy protocols
- quorum reads/writes
- CRDTs

---

## 9. Related Concepts

[[Strong Consistency]]
[[Synchronous Replication]]
[[Asynchronous Replication]]
[[Conflict Resolution]]
[[Quorums]]

---

## 10. Interview Questions

- What is eventual consistency?
- Why is it used in distributed systems?
- How do systems converge?
- What are its weaknesses?

---

## 11. Summary

Eventual consistency allows distributed systems to remain available during failures by permitting temporary divergence across replicas while guaranteeing eventual convergence.