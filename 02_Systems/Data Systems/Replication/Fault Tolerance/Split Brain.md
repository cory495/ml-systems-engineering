---
Created: 2026-06-27
Updated: 2026-06-27
tags:
  - systems
  - distributed-systems
  - fault-tolerance
Type: Notes
---

# Split Brain

Date: 2026-06-27

---

## 1. Problem

In distributed systems, network partitions can cause clusters to split into isolated groups that each believe they are the primary system.

This leads to multiple leaders or writers operating independently, causing inconsistent state.

---

## 2. Intuition

Split brain is “two brains thinking they are in control.”

Each side of a partition continues operating, unaware of the other, leading to divergence.

---

## 3. How It Works

Occurs when:
- network partition divides cluster
- both sides believe they have quorum or leadership
- writes proceed independently

Result:
- conflicting writes
- divergent system states
- difficult reconciliation after partition heals

---

## 4. Key Components

- cluster membership system
- leader election mechanism
- quorum rules
- network communication layer

---

## 5. Tradeoffs

### Pros
- none (this is a failure mode)

### Cons
- data inconsistency
- potential data loss
- conflicting writes
- difficult recovery

---

## 6. Scaling / Complexity

Risk increases with:

$$
P(\text{split brain}) \propto \text{network partitions} + \text{weak consensus}
$$

---

## 7. Real Systems Usage

- improperly configured clusters
- weak consensus systems
- poorly designed failover systems

---

## 8. Failure Modes

- dual leaders writing conflicting updates
- irreversible divergence in state
- corruption of replicated data
- difficult post-recovery reconciliation

Mitigations:
- strict quorum enforcement
- fencing tokens
- consensus protocols (Raft/Paxos)
- single-leader design

---

## 9. Related Concepts

[[Network Partitions]]
[[Quorums]]
[[Failover]]
[[Conflict Resolution]]
[[CAP Theorem]]

---

## 10. Interview Questions

- What is split brain?
- How does it occur?
- How do quorums prevent it?
- Why is it dangerous in distributed systems?

---

## 11. Summary

Split brain occurs when network partitions cause multiple nodes to act as independent leaders, resulting in conflicting writes and inconsistent system state.