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
# Secondary Index

Date: 2026-06-15

---

## 1. Problem

How do we efficiently query data using non-primary attributes?

Primary keys alone are insufficient for flexible querying.

---

## 2. Intuition

A secondary index is an additional index on a non-primary attribute.

It allows fast lookup by any column, not just the primary key.

---

## 3. How It Works

- Step 1: Choose secondary attribute (e.g. email, timestamp)
- Step 2: Build index mapping attribute → record pointers
- Step 3: Maintain index on updates
- Step 4: Query via index lookup

---

## 4. Key Components

- Secondary key
- Pointer(s) to rows
- Underlying index structure
- Update mechanism

---

## 5. Tradeoffs

### Pros
- Flexible querying
- Faster reads on non-primary fields

### Cons
- Additional storage
- Slower writes
- Maintenance overhead

---

## 6. Scaling / Complexity

### Lookup
O(log n)

### Insert
O(log n)

---

## 7. Real Systems Usage

- PostgreSQL secondary indexes
- MongoDB field indexes
- Elasticsearch inverted indexes
- Analytics databases

---

## 8. Failure Modes

- Too many secondary indexes → write slowdown
- Stale indexes
- Poor selectivity → ineffective index usage

---

## 9. Related Concepts

[[Indexes]]
[[Primary Index]]
[[Dense Index]]
[[Sparse Index]]

---

## 10. Interview Questions

- What is a secondary index?
- Why are secondary indexes expensive?
- Can you have multiple secondary indexes?

---

## 11. Summary

Secondary indexes enable fast querying on non-primary attributes but increase write cost and storage overhead.