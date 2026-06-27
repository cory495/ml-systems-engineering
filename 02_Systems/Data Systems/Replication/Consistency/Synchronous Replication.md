---
Created: 2026-06-27
Updated: 2026-06-27
tags:
  - systems
  - distributed-systems
  - consistency
Type: Notes
---

# Synchronous Replication

Date: 2026-06-27

---

## 1. Problem

In distributed systems, data is replicated across multiple nodes for reliability and availability. However, writes can be acknowledged before replicas are updated, leading to inconsistency.

We need a replication strategy that guarantees all replicas are updated before confirming a write.

---

## 2. Intuition

Synchronous replication is “wait for everyone before saying yes.”

A write is only successful when all (or required replicas) confirm the update.

This prioritizes correctness over latency.

---

## 3. How It Works

1. Client sends write to primary node
2. Primary forwards write to all replicas
3. Replicas persist the write
4. Replicas acknowledge success
5. Primary confirms write to client only after acknowledgments

---

## 4. Key Components

- primary node
- replica nodes
- acknowledgment protocol
- write barrier
- replication log

---

## 5. Tradeoffs

### Pros
- strong consistency across replicas
- no stale reads immediately after write
- simpler reasoning about correctness

### Cons
- high latency (slowest replica determines speed)
- reduced availability under failure
- sensitive to network partitions

---

## 6. Scaling / Complexity

Write latency:

$$
O(\max_{i \in replicas} latency_i)
$$

Availability decreases as replica count increases.

---

## 7. Real Systems Usage

- traditional relational databases with sync replication modes
- financial systems requiring strict correctness
- strongly consistent distributed databases (CP systems)

---

## 8. Failure Modes

- slow replica blocking writes
- cascading latency spikes
- unavailability during partial outages
- increased tail latency under load

Mitigations:
- quorum-based alternatives
- semi-synchronous replication
- replica timeout policies

---

## 9. Related Concepts

[[Asynchronous Replication]]
[[Semi-Synchronous Replication]]
[[Strong Consistency]]
[[Eventual Consistency]]
[[Quorums]]

---

## 10. Interview Questions

- What is synchronous replication?
- Why does it increase latency?
- How does it behave under a slow replica?
- When would you choose it over asynchronous replication?

---

## 11. Summary

Synchronous replication ensures all replicas confirm a write before acknowledgment, providing strong consistency at the cost of higher latency and reduced availability under failure conditions.