---
Created: 2026-06-27
Updated: 2026-06-27
tags:
  - systems
  - distributed-systems
  - fault-tolerance
Type: Concept
---

# CAP Theorem

Date: 2026-06-27

---

## 1. Problem

Distributed systems must operate under network partitions, but cannot simultaneously guarantee perfect consistency and availability in all scenarios.

We need a formal way to reason about these tradeoffs.

---

## 2. Intuition

CAP theorem states that when a network partition occurs, a system must choose between:

- **Consistency (C):** all nodes see the same data
- **Availability (A):** every request gets a response
- **Partition tolerance (P):** system continues operating despite network splits

Since partitions are inevitable, systems must trade off C vs A during failures.

---

## 3. How It Works

During a partition:

- If system chooses consistency:
  - some requests are rejected or delayed
- If system chooses availability:
  - responses may be stale or inconsistent

Normal operation may appear to satisfy both, but under partition the tradeoff becomes explicit.

---

## 4. Key Components

- distributed nodes
- replication protocol
- consensus mechanism
- failure detection system

---

## 5. Tradeoffs

### CP systems
- strong consistency
- reduced availability under partition

### AP systems
- high availability
- eventual consistency

### CA systems
- not realistic in distributed environments with partitions

---

## 6. Scaling / Complexity

CAP is not computational but conceptual:

System behavior depends on:
- partition frequency
- replication latency
- quorum design

---

## 7. Real Systems Usage

- CP systems: Zookeeper, etcd
- AP systems: Dynamo, Cassandra (tunable consistency)
- hybrid systems: most modern databases

---

## 8. Failure Modes

- misunderstanding CAP as “choose 2 of 3”
- incorrect assumption that CA systems exist in distributed settings
- misconfigured quorum leading to unintended behavior

Mitigations:
- explicit consistency models
- tunable quorum systems
- clear SLA definitions

---

## 9. Related Concepts

[[Network Partitions]]
[[Quorums]]
[[Consistency Models]]
[[Conflict Resolution]]
[[Failover]]

---

## 10. Interview Questions

- What does CAP theorem actually state?
- Why is partition tolerance non-negotiable?
- What is the tradeoff between consistency and availability?
- How do real systems implement CAP tradeoffs?

---

## 11. Summary

CAP theorem formalizes the tradeoff in distributed systems that during network partitions, systems must choose between consistency and availability while always accounting for partition tolerance as a fundamental constraint.