---
Created: 2026-06-27
Updated: 2026-06-27
tags:
  - systems
  - distributed-systems
  - scaling
Type: Notes
---

# Hotspots

Date: 2026-06-27

---

## 1. Problem

In distributed systems, some partitions or nodes receive disproportionately high traffic compared to others.

This leads to bottlenecks that degrade system performance even when overall capacity is sufficient.

---

## 2. Intuition

A hotspot is a “traffic jam” in one part of the system.

Even if the road network is large, one congested intersection can slow everything down.

---

## 3. How It Works

Hotspots occur when:
- a key becomes extremely popular
- partitioning function is skewed
- workload is not uniformly distributed

Detection:
- high QPS per shard
- elevated latency on specific nodes
- CPU or I/O saturation

---

## 4. Key Components

- skewed keys
- partition function
- load distribution metrics
- caching layers

---

## 5. Tradeoffs

### Pros
- none inherently (it is a failure mode)

### Cons
- degraded latency
- uneven resource utilization
- cascading failures under load

---

## 6. Scaling / Complexity

Hotspot cost is localized but severe:

$$
O(n) \text{ load concentration on single partition}
$$

---

## 7. Real Systems Usage

- viral content in social media systems
- popular product pages in e-commerce
- trending hashtags
- shard key skew in databases

---

## 8. Failure Modes

- single shard overload
- cascading retries amplifying load
- cache stampedes
- leader node saturation

Mitigations:
- request sharding (key salting)
- caching layers
- adaptive partitioning
- rate limiting

---

## 9. Related Concepts

[[Data Skew]]
[[Partition Rebalancing]]
[[Dynamic Partitioning]]
[[Fixed Partitioning]]

---

## 10. Interview Questions

- What causes hotspots?
- How do you mitigate hot partitions?
- Why does consistent hashing not always prevent hotspots?

---

## 11. Summary

Hotspots are uneven load concentrations in distributed systems that create bottlenecks and latency spikes. They are typically caused by skewed access patterns and require mitigation through partitioning, caching, and load distribution strategies.