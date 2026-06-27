---
Created: 2026-06-27
Updated: 2026-06-27
tags:
  - systems
  - distributed-systems
  - fault-tolerance
Type: Concept
---

# Network Partitions

Date: 2026-06-27

---

## 1. Problem

Distributed systems rely on communication between nodes, but networks are unreliable and can fail in unpredictable ways.

We need to understand and handle situations where nodes cannot communicate.

---

## 2. Intuition

A network partition is “the cluster being split into isolated islands.”

Each side continues operating but cannot coordinate with the other.

---

## 3. How It Works

Causes:
- link failures
- packet loss
- routing issues
- datacenter outages

Effects:
- nodes cannot communicate across partition boundary
- system behaves as separate subclusters

---

## 4. Key Components

- network links
- cluster membership
- replication channels
- coordination protocol

---

## 5. Tradeoffs

### Pros
- none (it is a failure condition)

### Cons
- inconsistent system state
- split brain risk
- degraded availability or consistency

---

## 6. Scaling / Complexity

Probability of partition increases with:

$$
P \uparrow \text{ as system size and network complexity increase}
$$

---

## 7. Real Systems Usage

- cloud distributed systems
- multi-region databases
- microservice architectures
- Kubernetes clusters

---

## 8. Failure Modes

- split brain
- stale reads/writes
- quorum loss leading to unavailability
- cascading failures across regions

Mitigations:
- quorum-based systems
- consensus protocols
- replication strategies
- failover mechanisms

---

## 9. Related Concepts

[[Quorums]]
[[Split Brain]]
[[Failover]]
[[CAP Theorem]]
[[Anti-Entropy]]

---

## 10. Interview Questions

- What is a network partition?
- Why are partitions inevitable in distributed systems?
- How do systems behave under partitions?
- How does CAP theorem relate?

---

## 11. Summary

Network partitions occur when nodes in a distributed system cannot communicate, forcing systems to choose between consistency and availability and making fault tolerance a core design requirement.