---
Created: 2026-06-27
Updated: 2026-06-27
tags:
  - systems
  - distributed-systems
  - scaling
  - partitioning
Type: Notes
---

# Fixed Partitioning

Date: 2026-06-27

---

## 1. Problem

We need a simple and predictable way to distribute data across multiple nodes.

Without partitioning, a single node becomes a bottleneck for storage and traffic.

---

## 2. Intuition

Fixed partitioning is static sharding.

Data is divided using a predefined rule (hash or range), and that rule never changes.

It prioritizes simplicity and predictability over adaptability.

---

## 3. How It Works

Common strategies:

### Hash-based
$$
partition = hash(key) \mod N
$$

### Range-based
Keys are split into ordered intervals assigned to nodes.

Once assigned, partitions remain fixed.

---

## 4. Key Components

- partition function
- shard map
- routing layer
- storage nodes

---

## 5. Tradeoffs

### Pros
- simple to implement
- predictable routing
- low metadata overhead

### Cons
- poor adaptability to workload changes
- hotspots can persist
- expensive rebalancing when scaling

---

## 6. Scaling / Complexity

Routing:

$$
O(1)
$$

Repartitioning cost (when scaling):

$$
O(n)
$$

---

## 7. Real Systems Usage

- early-stage distributed databases
- simple cache systems (Redis clustering modes)
- baseline sharding strategies in many systems

---

## 8. Failure Modes

- hotspot partitions under skewed access patterns
- expensive cluster resizing
- uneven data distribution over time

Mitigations:
- consistent hashing
- virtual nodes
- overprovisioning

---

## 9. Related Concepts

[[Dynamic Partitioning]]
[[Partition Rebalancing]]
[[Data Skew]]
[[Hotspots]]
[[Routing Layer]]

---

## 10. Interview Questions

- What is fixed partitioning?
- Why is it simple but limited?
- How does it behave under skewed workloads?

---

## 11. Summary

Fixed partitioning divides data using a static rule that does not change over time. It is simple and efficient but does not adapt well to workload shifts or evolving data distributions.