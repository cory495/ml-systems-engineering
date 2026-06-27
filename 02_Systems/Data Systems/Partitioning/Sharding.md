---
Created: 2026-06-27
Updated: 2026-06-27
tags:
  - systems
  - distributed-systems
  - partitioning
Type: Notes
---

# Sharding

Date: 2026-06-27

---

## 1. Problem

A single database instance cannot handle unlimited scale in storage, throughput, or availability.

We need a strategy to distribute data across multiple independent database nodes.

---

## 2. Intuition

Sharding is “horizontal partitioning applied in a distributed system.”

Each shard is a fully independent database instance responsible for a subset of the data.

Think:
> “many small databases instead of one large one”

---

## 3. How It Works

1. Choose shard key (user_id, tenant_id, etc.)
2. Apply partition function:
   - hash-based
   - range-based
   - consistent hashing
3. Route requests via shard map
4. Store each shard independently
5. Rebalance shards as system scales

---

## 4. Key Components

- shard key
- routing layer
- shard map / metadata service
- individual database nodes
- rebalancing system

---

## 5. Tradeoffs

### Pros
- near-linear scalability
- fault isolation per shard
- improved write throughput

### Cons
- cross-shard queries are expensive
- operational complexity increases significantly
- rebalancing is expensive and risky

---

## 6. Scaling / Complexity

Single shard lookup:

$$
O(1)
$$

Cross-shard query:

$$
O(n)
$$

Rebalancing:

$$
O(k)
$$

---

## 7. Real Systems Usage

- MongoDB sharding
- Cassandra clusters
- Dynamo-style systems
- large-scale SaaS multi-tenant systems

---

## 8. Failure Modes

- hotspot shards
- uneven shard distribution
- expensive resharding operations
- metadata inconsistency during scaling events

Mitigations:
- consistent hashing
- virtual nodes
- automated rebalancing
- caching layers

---

## 9. Related Concepts

[[Partitioning]]
[[Horizontal Partitioning]]
[[Consistent Hashing]]
[[Routing Layer]]
[[Metadata Service]]

---

## 10. Interview Questions

- What is sharding?
- How is it different from partitioning?
- How do you choose a shard key?
- What happens when a shard becomes too large?

---

## 11. Summary

Sharding is the distributed systems implementation of horizontal partitioning, where data is split across independent database nodes to achieve scalability, fault isolation, and high throughput.