---
Created: 2026-06-01
Updated: 2026-06-26
tags:
  - systems
  - programming
  - databases
Type: Notes
---
# B+ Tree

Date: 2026-06-15

---

## 1. Problem

How can we support efficient **range queries and ordered scans** while still maintaining fast lookups and updates?

A standard B-Tree can do this, but database systems optimize further for disk access patterns.

---

## 2. Intuition

A B+ Tree is an improvement over a B-Tree where:

> All actual data is stored at the leaf level, and internal nodes only store keys for navigation.

This makes traversal predictable and range queries extremely efficient.

Think of it like:

- Internal nodes = roadmap
- Leaf nodes = actual data

---

## 3. How It Works

- Step 1: Start at root node
- Step 2: Traverse internal nodes using key comparisons
- Step 3: Reach leaf node containing data pointers
- Step 4: Follow linked leaf nodes for range scans

Key difference:

- B-Tree: data stored in internal + leaf nodes
- B+ Tree: data only in leaf nodes

---

## 4. Key Components

- Root node
- Internal index nodes
- Leaf nodes (linked list)
- Sorted keys
- Pointers to records

---

## 5. Tradeoffs

### Pros

- Excellent range query performance
- Predictable disk access
- Better cache efficiency
- Simplified traversal logic

### Cons

- Slightly more storage overhead
- Deeper leaf-level access for point lookups

### When NOT to use it

- Pure key-value workloads where range queries are irrelevant

---

## 6. Scaling / Complexity

### Lookup
O(log n)

### Range scan
O(log n + k)

(where k = number of results)

### Bottlenecks
- Tree height
- Disk page reads
- Pointer chasing

---

## 7. Real Systems Usage

- PostgreSQL indexes
- MySQL InnoDB
- SQLite
- Oracle DB

---

## 8. Failure Modes

- Page splits under heavy writes
- Fragmentation
- Cache misses in upper levels
- Poor locality for large trees

---

## 9. Related Concepts

[[B-Tree]]
[[Page Structure]]
[[Range Queries]]
[[Indexes]]

---

## 10. Interview Questions

- Why do databases use B+ Trees instead of B-Trees?
- Why store data only in leaves?
- Why are B+ Trees good for range scans?

---

## 11. Summary

A B+ Tree is a disk-optimized search tree where all data resides in leaf nodes, enabling highly efficient range queries and predictable traversal patterns.