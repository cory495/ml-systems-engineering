---
Created: 2026-06-01
Updated: 2026-06-26
tags:
  - systems
  - programming
  - databases
  - distributed-systems
Type: Notes
---
# Hash Index

Date: 2026-06-15

---

## 1. Problem

How can we support extremely fast exact-match lookups?

We want to find values by key without scanning or traversing a tree.

---

## 2. Intuition

A hash index uses a hash function to map keys directly to storage locations.

Think:

> key → hash → bucket → value

It is optimized for equality checks, not ordering.

![[pic_hash_indexes.png]]

---

## 3. How It Works

- Step 1: Hash the key
- Step 2: Map to bucket
- Step 3: Store pointer/value in bucket
- Step 4: Resolve collisions if needed

---

## 4. Key Components

- Hash function
- Buckets
- Collision resolution (chaining or probing)
- Key-value pointers

---

## 5. Tradeoffs

### Pros
- O(1) average lookup
- Very fast for equality queries

### Cons
- No support for range queries
- Poor cache locality in some cases
- Collision overhead

### When NOT to use it
- Range queries
- Ordered scans
- Analytics workloads

---

## 6. Scaling / Complexity

### Lookup
O(1) average, O(n) worst case

### Insert
O(1) average

### Space
O(n)

---

## 7. Real Systems Usage

- Redis (hash tables)
- Hash indexes in databases
- In-memory key-value stores
- Dynamo-style systems (partial use)

---

## 8. Failure Modes

- Hash collisions → degraded performance
- Load factor too high → resizing overhead
- Poor hash function → clustering

---

## 9. Related Concepts

[[Indexes]]
[[Primary Index]]
[[Secondary Index]]
[[Sparse Index]]
[[Dense Index]]

---

## 10. Interview Questions

- Why are hash indexes fast?
- Why don’t databases use hash indexes for everything?
- What is a collision?

---

## 11. Summary

Hash indexes provide fast equality lookups using hashing but do not support ordering or range queries.