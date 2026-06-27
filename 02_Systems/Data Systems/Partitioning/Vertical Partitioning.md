---
Created: 2026-06-27
Updated: 2026-06-27
tags:
  - systems
  - databases
  - partitioning
Type: Notes
---

# Vertical Partitioning

Date: 2026-06-27

---

## 1. Problem

Large tables often contain many columns, but most queries only access a subset of them.

Storing all columns together leads to unnecessary I/O, memory usage, and cache inefficiency.

We need a way to split data by columns rather than rows.

---

## 2. Intuition

Vertical partitioning splits a table **by columns**.

Each partition stores a subset of attributes for the same entities.

Think:
- one table = identity data
- another = profile data
- another = analytics data

---

## 3. How It Works

1. Identify frequently accessed column groups
2. Split table into multiple narrower tables
3. Use a shared primary key to join partitions when needed
4. Route queries to relevant column group only

---

## 4. Key Components

- primary key (join key)
- column groups
- storage partitions
- join layer (application or database)

---

## 5. Tradeoffs

### Pros
- reduced I/O per query
- better cache efficiency
- improved performance for narrow reads

### Cons
- requires joins for full records
- increased query complexity
- potential write amplification across partitions

---

## 6. Scaling / Complexity

Single-column group read:

$$
O(k)
$$

Full reconstruction:

$$
O(n \log n) \text{ depending on join strategy}
$$

---

## 7. Real Systems Usage

- wide column stores (conceptually opposite but related idea)
- user profile systems
- analytics systems separating hot vs cold fields
- privacy-sensitive data separation

---

## 8. Failure Modes

- expensive joins on full record access
- inconsistent updates across partitions
- schema evolution complexity
- fragmentation of related data

Mitigations:
- careful column grouping
- denormalization where appropriate
- materialized views

---

## 9. Related Concepts

[[Partitioning]]
[[Horizontal Partitioning]]
[[Sharding]]
[[Secondary Index]]

---

## 10. Interview Questions

- What is vertical partitioning?
- When is it better than horizontal partitioning?
- What are the tradeoffs of splitting columns?

---

## 11. Summary

Vertical partitioning splits a table by columns to optimize I/O and performance, but introduces join complexity and increases system design overhead.