---
Created: 2026-06-27
Updated: 2026-06-27
tags:
  - systems
  - distributed-systems
  - fault-tolerance
Type: Concept
---

# Quorums

Date: 2026-06-27

---

## 1. Problem

In distributed systems, replicas can diverge due to failures, latency, or network partitions.

We need a way to make decisions (reads/writes) without requiring all nodes to agree, while still maintaining correctness guarantees.

---

## 2. Intuition

A quorum is “majority agreement.”

Instead of waiting for all replicas, the system only requires a subset large enough to guarantee overlap between read and write operations.

This ensures consistency even when some nodes are down or partitioned.

---

## 3. How It Works

In a system with \(N\) replicas:

- Write quorum: \(W\)
- Read quorum: \(R\)

Correctness condition:

$$
R + W > N
$$

This ensures at least one overlapping replica between reads and writes.

---

## 4. Key Components

- replica set
- quorum size configuration
- coordinator node
- replication protocol
- versioning/timestamps

---

## 5. Tradeoffs

### Pros
- high availability
- tunable consistency
- fault tolerance under partial failure

### Cons
- higher latency than single-node reads
- complex configuration tuning
- degraded performance under failures

---

## 6. Scaling / Complexity

Read/write latency depends on quorum size:

$$
O(W), \quad O(R)
$$

Failure tolerance:

$$
\text{can tolerate } N - W \text{ write failures}
$$

---

## 7. Real Systems Usage

- Dynamo-style databases
- Cassandra
- Riak
- distributed key-value stores
- quorum-based replication systems

---

## 8. Failure Modes

- stale reads if quorum condition violated
- write amplification under high W
- availability loss during partitions
- misconfigured quorum parameters

Mitigations:
- careful tuning of \(R/W\)
- hinted handoff
- replica repair mechanisms

---

## 9. Related Concepts

[[Read Repair]]
[[Anti-Entropy]]
[[Conflict Resolution]]
[[Network Partitions]]
[[CAP Theorem]]

---

## 10. Interview Questions

- What is a quorum?
- Why does \(R + W > N\) matter?
- How do quorums handle failures?
- What are tradeoffs in choosing R and W?

---

## 11. Summary

Quorums enable distributed systems to maintain consistency and availability under partial failures by requiring overlapping subsets of replicas to agree on reads and writes.