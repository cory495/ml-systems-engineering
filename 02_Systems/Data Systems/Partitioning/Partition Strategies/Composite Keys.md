---
Created: 2026-06-27
Updated: 2026-06-27
tags:
  - systems
  - distributed-systems
  - partitioning
Type: Notes
---

# Composite Keys

Date: 2026-06-27

---

## 1. Problem

Single-key partitioning often fails to capture multi-dimensional access patterns, leading to hotspots or inefficient queries.

We need a way to encode multiple attributes into a single partitioning strategy.

---

## 2. Intuition

A composite key combines multiple fields into one logical key.

It allows partitioning schemes to reflect richer structure than a single attribute.

Think:
> “multi-dimensional routing collapsed into one key”

---

## 3. How It Works

A composite key might look like:

$$
key = (user\_id, timestamp)
$$

Or encoded as:

$$
key = user\_id \; || \; timestamp
$$

Partitioning can then be based on:
- prefix (user_id)
- full hash
- hierarchical splitting

---

## 4. Key Components

- primary component (partition key)
- secondary component (sort key)
- encoding strategy
- query pattern alignment

---

## 5. Tradeoffs

### Pros
- flexible query design
- reduces hotspots when designed well
- supports range + locality queries

### Cons
- complex schema design
- requires query-aware partitioning
- poor design leads to severe skew

---

## 6. Scaling / Complexity

Depends on partitioning scheme:

- hash-based composite: \(O(1)\)
- range-based composite: \(O(\log n)\)

---

## 7. Real Systems Usage

- DynamoDB partition + sort keys
- Bigtable row keys
- time-series systems (user + timestamp)
- event logging systems

---

## 8. Failure Modes

- poor key design causing hotspots
- unbounded growth in sort dimension
- inefficient query access patterns

Mitigations:
- key salting
- careful schema design
- access-pattern-driven modeling

---

## 9. Related Concepts

[[Hash Partitioning]]
[[Key Range Partitioning]]
[[Consistent Hashing]]
[[Data Skew]]
[[Hotspots]]

---

## 10. Interview Questions

- What is a composite key?
- How does key design affect partitioning?
- Why do bad composite keys cause hotspots?

---

## 11. Summary

Composite keys combine multiple attributes into a single key structure, enabling flexible partitioning and query patterns but requiring careful design to avoid skew and hotspots.