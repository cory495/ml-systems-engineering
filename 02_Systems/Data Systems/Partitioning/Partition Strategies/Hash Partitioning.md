---
Created: 2026-06-27
Updated: 2026-06-27
tags:
  - systems
  - distributed-systems
  - partitioning
Type: Notes
---

# Hash Partitioning

Date: 2026-06-27

---

## 1. Problem

We need a simple and uniform way to distribute data across nodes while avoiding hotspots caused by ordered keys.

---

## 2. Intuition

Hash partitioning spreads data randomly across nodes using a hash function.

Instead of grouping similar keys, it distributes them uniformly.

Think:
> “randomize everything to avoid clustering”

---

## 3. How It Works

1. Compute hash of key:
$$
h = hash(key)
$$

2. Assign partition:
$$
partition = h \mod N
$$

3. Route request to corresponding node

---

## 4. Key Components

- hash function
- modulo or bucket mapping
- partition table
- routing layer

---

## 5. Tradeoffs

### Pros
- even distribution of load
- simple implementation
- avoids range-based hotspots

### Cons
- poor range query support
- expensive rebalancing when N changes
- loss of data locality

---

## 6. Scaling / Complexity

Lookup:

$$
O(1)
$$

Repartitioning:

$$
O(n)
$$

if number of partitions changes.

---

## 7. Real Systems Usage

- distributed caches (Redis Cluster)
- Dynamo-style databases
- load balancing systems
- key-value stores

---

## 8. Failure Modes

- partition churn when scaling nodes
- hash function bias (poor distribution)
- hot keys still possible (skewed access patterns)

Mitigations:
- consistent hashing
- virtual nodes
- better hash functions

---

## 9. Related Concepts

[[Key Range Partitioning]]
[[Consistent Hashing]]
[[Composite Keys]]
[[Data Skew]]
[[Hotspots]]

---

## 10. Interview Questions

- Why use hash partitioning?
- What problem does it solve vs range partitioning?
- What happens when you add a node?

---

## 11. Summary

Hash partitioning distributes data uniformly using a hash function, providing good load balance but sacrificing range query efficiency and rebalancing simplicity.