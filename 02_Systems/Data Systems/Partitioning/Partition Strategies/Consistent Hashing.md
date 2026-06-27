---
Created: 2026-06-27
Updated: 2026-06-27
tags:
  - systems
  - distributed-systems
  - partitioning
Type: Notes
---

# Consistent Hashing

Date: 2026-06-27

---

## 1. Problem

In hash partitioning, adding or removing nodes causes massive data reshuffling.

We need a partitioning scheme where node changes only affect a small portion of the keyspace.

---

## 2. Intuition

Consistent hashing places both keys and nodes on a circular hash space (“ring”).

Each key maps to the nearest node clockwise.

When nodes change, only neighboring regions are affected.

---

## 3. How It Works

1. Hash nodes onto a ring:
$$
hash(node)
$$

2. Hash keys onto same ring:
$$
hash(key)
$$

3. Assign key to next clockwise node

4. When node is added/removed:
- only adjacent segments remapped

---

## 4. Key Components

- hash ring
- virtual nodes
- key placement strategy
- node membership tracking

---

## 5. Tradeoffs

### Pros
- minimal rebalancing
- scalable node changes
- widely used in distributed systems

### Cons
- more complex implementation
- uneven distribution without virtual nodes
- harder to reason about

---

## 6. Scaling / Complexity

Lookup:

$$
O(\log n)
$$

(using sorted ring structure)

---

## 7. Real Systems Usage

- Amazon Dynamo
- Cassandra
- distributed caches (Memcached variants)
- load balancing systems

---

## 8. Failure Modes

- uneven load without virtual nodes
- ring imbalance under skew
- metadata synchronization issues

Mitigations:
- virtual nodes
- weighted hashing
- rebalancing strategies

---

## 9. Related Concepts

[[Hash Partitioning]]
[[Key Range Partitioning]]
[[Composite Keys]]
[[Partition Rebalancing]]

---

## 10. Interview Questions

- Why is consistent hashing better than modulo hashing?
- What happens when a node joins?
- Why are virtual nodes needed?

---

## 11. Summary

Consistent hashing maps keys and nodes onto a ring to minimize data movement when nodes change, making it a foundational technique for scalable distributed systems.