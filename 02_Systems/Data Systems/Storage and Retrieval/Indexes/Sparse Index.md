---
Created: 2026-06-01
Updated: 2026-06-26
tags:
  - systems
  - programming
  - databases
Type: Notes
---
# Sparse Index

Date: 2026-06-15

---

## 1. Problem

How can we reduce index size while still enabling efficient lookups?

Storing an index entry for every record can be expensive.

---

## 2. Intuition

A sparse index only stores **some keys**, not all of them.

Typically, it stores one entry per block or page instead of per record.

It relies on underlying sorted storage.

---

## 3. How It Works

- Step 1: Store index entries at intervals (e.g., per page)
- Step 2: Use index to jump close to target location
- Step 3: Scan locally within block to find exact record

---

## 4. Key Components

- Block-level pointers
- Sorted data file
- Sampling strategy
- Page alignment

---

## 5. Tradeoffs

### Pros
- Smaller index size
- Lower memory usage
- Faster index updates

### Cons
- Requires scanning within blocks
- Slightly slower lookups than dense index

### When NOT to use it
- Highly random access patterns without locality

---

## 6. Scaling / Complexity

### Lookup
O(log n + block size scan)

### Space
Much smaller than dense index

---

## 7. Real Systems Usage

- SSTables (LSM trees)
- Log-structured storage
- Some B-Tree optimizations
- Large-scale databases

---

## 8. Failure Modes

- Large block sizes → slower scans
- Poor clustering → inefficient lookups

---

## 9. Related Concepts

[[Dense Index]]
[[Indexes]]
[[SSTable]]
[[Page Structure]]

---

## 10. Interview Questions

- Why use sparse instead of dense index?
- What tradeoff does sparse indexing introduce?
- Where is sparse indexing commonly used?

---

## 11. Summary

Sparse indexes reduce storage overhead by indexing only selected keys, trading slightly slower lookups for efficiency.