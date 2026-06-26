---
Created: 2026-06-01
Updated: 2026-06-26
tags:
  - systems
  - programming
  - databases
Type: Notes
---
# Dense Index

Date: 2026-06-15

---

## 1. Problem

How can we guarantee fast lookup for every record in a dataset?

---

## 2. Intuition

A dense index contains an entry for **every record in the dataset**.

It provides direct mapping from key → record location.

---

## 3. How It Works

- Step 1: Store index entry for every key
- Step 2: Maintain pointer to each record
- Step 3: Use index for direct lookup

---

## 4. Key Components

- One entry per record
- Key-to-pointer mapping
- Underlying storage structure

---

## 5. Tradeoffs

### Pros
- Fastest possible lookups
- Simple retrieval logic

### Cons
- Large memory overhead
- Expensive to maintain
- Slower writes

### When NOT to use it
- Very large datasets where memory is limited

---

## 6. Scaling / Complexity

### Lookup
O(log n) or O(1) depending on structure

### Space
O(n) (larger than sparse index)

---

## 7. Real Systems Usage

- B-Tree leaf-level indexing
- In-memory databases
- High-performance OLTP systems

---

## 8. Failure Modes

- Index bloat
- Memory pressure
- Write amplification

---

## 9. Related Concepts

[[Sparse Index]]
[[Indexes]]
[[B-Tree]]
[[Primary Index]]

---

## 10. Interview Questions

- Dense vs sparse index?
- Why not always use dense indexes?
- What are the memory tradeoffs?

---

## 11. Summary

Dense indexes store a mapping for every record, enabling fast lookups at the cost of higher storage and maintenance overhead.