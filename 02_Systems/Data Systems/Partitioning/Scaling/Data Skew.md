---
Created: 2026-06-27
Updated: 2026-06-27
tags:
  - systems
  - distributed-systems
  - scaling
Type: Notes
---

# Data Skew

Date: 2026-06-27

---

## 1. Problem

Distributed systems assume relatively uniform data and request distribution.

In reality, data and traffic are often heavily imbalanced, causing inefficient resource utilization and performance degradation.

---

## 2. Intuition

Data skew is “uneven distribution of work.”

Some keys or partitions receive far more traffic or data than others, breaking assumptions of balanced load.

---

## 3. How It Works

Skew arises from:
- non-uniform key distributions (Zipfian patterns)
- correlated access patterns
- poor partitioning functions
- real-world popularity distributions

Effects:
- uneven partition sizes
- uneven query load
- degraded tail latency

---

## 4. Key Components

- key distribution
- partitioning strategy
- workload patterns
- access frequency distribution

---

## 5. Tradeoffs

### Pros
- none inherently (it is a system challenge)

### Cons
- load imbalance
- inefficient scaling
- hotspot formation
- wasted capacity on underutilized nodes

---

## 6. Scaling / Complexity

Skew increases effective load:

$$
\max(\text{load}_i) \gg \text{avg load}
$$

Worst case:

$$
O(n) \text{ concentration on a single partition}
$$

---

## 7. Real Systems Usage

- social media trending content
- user ID-based access skew
- product catalogs in e-commerce
- event logging systems

---

## 8. Failure Modes

- severe hotspot formation
- unpredictable latency spikes
- poor autoscaling behavior
- uneven storage growth

Mitigations:
- salting keys
- adaptive partitioning
- load-aware routing
- caching hot keys

---

## 9. Related Concepts

[[Hotspots]]
[[Partition Rebalancing]]
[[Dynamic Partitioning]]
[[Fixed Partitioning]]

---

## 10. Interview Questions

- What is data skew?
- How does skew affect partitioning?
- How would you design a system to handle skewed workloads?

---

## 11. Summary

Data skew is the uneven distribution of data or requests across a distributed system, leading to imbalance, hotspots, and degraded performance if not mitigated through careful partitioning and load balancing strategies.