---
Created: 2026-06-01
Updated: 2026-06-26
tags:
  - systems
  - programming
  - databases
Type: Notes
---
# Primary Index

Date: 2026-06-15

---

## 1. Problem

How do we efficiently locate records when the table itself is organized by a key?

---

## 2. Intuition

A primary index is built on the primary key of a table.

In clustered storage systems, the primary index often determines physical row order.

---

## 3. How It Works

- Step 1: Choose primary key
- Step 2: Organize data by key order (in clustered systems)
- Step 3: Build index structure on top
- Step 4: Use index for lookups and range scans

---

## 4. Key Components

- Primary key
- Clustered storage (optional)
- Index structure
- Row pointers

---

## 5. Tradeoffs

### Pros
- Efficient lookups
- Efficient range queries (if clustered)
- Natural ordering

### Cons
- Insertion overhead if ordered
- Rebalancing costs

---

## 6. Scaling / Complexity

### Lookup
O(log n)

### Insert
O(log n) or worse in clustered systems

---

## 7. Real Systems Usage

- MySQL InnoDB clustered primary key
- PostgreSQL primary key index
- SQL Server clustered index

---

## 8. Failure Modes

- Page splits
- Fragmentation
- Hotspot keys (monotonic inserts)

---

## 9. Related Concepts

[[Secondary Index]]
[[B+ Tree]]
[[Indexes]]
[[Page Structure]]

---

## 10. Interview Questions

- What is a primary index?
- What is clustering?
- Why are sequential keys problematic?

---

## 11. Summary

A primary index organizes data around the primary key, often determining physical storage order and enabling efficient lookups.