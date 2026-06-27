---
Created: 2026-06-27
Updated: 2026-06-27
tags:
  - systems
  - distributed-systems
  - consistency
Type: Notes
---

# Strong Consistency

Date: 2026-06-27

---

## 1. Problem

In distributed systems, concurrent reads and writes across replicas can lead to inconsistent views of data.

We need a model where all clients observe a single, correct, up-to-date view of the system.

---

## 2. Intuition

Strong consistency means “everyone sees the same latest truth.”

Once a write is acknowledged, all subsequent reads reflect that write immediately.

It behaves as if there is a single global state.

---

## 3. How It Works

Common implementations:

1. Single leader replication
2. Consensus protocols (Raft / Paxos)
3. Synchronous quorum writes

Key idea:
- ensure a global ordering of operations

---

## 4. Key Components

- leader node or consensus group
- log replication
- quorum agreement
- ordering mechanism (log sequence numbers)

---

## 5. Tradeoffs

### Pros
- simple mental model
- no stale reads
- deterministic system behavior

### Cons
- higher latency
- reduced availability under partitions
- complex consensus algorithms

---

## 6. Scaling / Complexity

Write latency:

$$
O(\text{consensus round})
$$

Typically bounded by slowest quorum participant.

---

## 7. Real Systems Usage

- etcd
- ZooKeeper
- strongly consistent SQL databases
- distributed lock services

---

## 8. Failure Modes

- unavailability during partitions
- leader election delays
- performance bottlenecks under heavy load
- split-brain if consensus fails

Mitigations:
- Raft/Paxos
- quorum enforcement
- fencing tokens

---

## 9. Related Concepts

[[Eventual Consistency]]
[[Synchronous Replication]]
[[Quorums]]
[[Failover]]
[[CAP Theorem]]

---

## 10. Interview Questions

- What is strong consistency?
- How does it differ from eventual consistency?
- What systems provide it?
- Why does it reduce availability?

---

## 11. Summary

Strong consistency guarantees that all reads reflect the most recent write by enforcing a single globally ordered state across replicas, typically via consensus or synchronous replication, at the cost of availability and latency.