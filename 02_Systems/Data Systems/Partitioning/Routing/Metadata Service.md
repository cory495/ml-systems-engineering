---
Created: 2026-06-27
Updated: 2026-06-27
tags:
  - systems
  - distributed-systems
  - metadata
Type: Notes
---

# Metadata Service

Date: 2026-06-27

---

## 1. Problem

Distributed systems need a consistent source of truth about:
- cluster topology
- partition maps
- replica locations
- service health

Without centralized metadata, routing becomes inconsistent and unsafe.

---

## 2. Intuition

A metadata service is the “brain” of a distributed system.

It tells every component:
> “Where everything is and how to reach it.”

---

## 3. How It Works

1. Nodes register themselves with metadata service
2. System updates:
   - partition ownership
   - replica assignments
   - health status
3. Clients or routing layers query metadata
4. Routing decisions are made using this information

Often implemented using consensus systems like:
- ZooKeeper
- etcd
- Consul

---

## 4. Key Components

- Cluster state store
- Partition map
- Node registry
- Health tracking
- Versioning system

---

## 5. Tradeoffs

### Pros
- single source of truth
- consistent routing decisions
- enables dynamic scaling

### Cons
- potential bottleneck
- requires strong consistency
- failure affects entire system

---

## 6. Scaling / Complexity

Reads:

$$
O(1)
$$

Updates:

$$
O(n) \text{ (broadcast or consensus dependent)}
$$

---

## 7. Real Systems Usage

- Kubernetes (etcd)
- distributed databases (Cassandra, Dynamo-like systems)
- service discovery systems
- load balancers
- LLM serving infrastructure

---

## 8. Failure Modes

- stale metadata causing incorrect routing
- split-brain scenarios
- consensus failures
- cascading system-wide outages

Mitigations:
- versioned metadata
- quorum-based consensus
- local caching with TTL
- fallback routing rules

---

## 9. Related Concepts

[[Routing Layer]]
[[Request Routing]]
[[Scatter Queries]]
[[Consensus Algorithms]]
[[Partitioning]]

---

## 10. Interview Questions

- Why do distributed systems need metadata services?
- What happens if metadata becomes inconsistent?
- How does etcd/ZooKeeper ensure consistency?
- What are tradeoffs between consistency and availability?

---

## 11. Summary

A metadata service is the authoritative system component that tracks cluster state and enables correct routing, scaling, and coordination in distributed systems.