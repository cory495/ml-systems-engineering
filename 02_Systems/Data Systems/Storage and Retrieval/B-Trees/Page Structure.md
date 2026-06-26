---
Created: 2026-06-01
Updated: 2026-06-26
tags:
  - systems
  - programming
  - databases
Type: Notes
---
# Page Structure

Date: 2026-06-15

---

## 1. Problem

How do databases efficiently read and write data on disk without excessive I/O overhead?

Disk access is slow, so databases must organize data to minimize reads and writes.

---

## 2. Intuition

Databases do not read individual rows from disk.

They read fixed-size **pages** (blocks of data), typically 4KB–16KB.

A page is the fundamental unit of I/O.

Think of it like:

> “You don’t read words from disk — you read pages.”

---

## 3. How It Works

- Step 1: Data is grouped into pages
- Step 2: Pages are read into memory (buffer pool)
- Step 3: Modifications happen in memory
- Step 4: Dirty pages are flushed back to disk

---

## 4. Key Components

- Page (fixed-size block)
- Buffer pool (cache)
- Page header (metadata)
- Slots / offsets (row location tracking)

---

## 5. Tradeoffs

### Pros

- Reduces disk I/O overhead
- Enables efficient caching
- Aligns with hardware behavior

### Cons

- Internal fragmentation
- Page splitting complexity
- Overhead for small updates

### When NOT to use it

Not applicable — all disk-based DBs use page structures.

---

## 6. Scaling / Complexity

### Read
O(1) per page (amortized via caching)

### Write
Depends on page modification and flushing

### Bottlenecks
- Page cache misses
- Random I/O
- Page splits

---

## 7. Real Systems Usage

- PostgreSQL (8KB pages)
- MySQL InnoDB (16KB pages)
- SQLite (variable pages)
- SQL Server

---

## 8. Failure Modes

- Page corruption
- Buffer pool overflow
- Frequent page splits
- Write amplification due to page rewrites

---

## 9. Related Concepts

[[B-Tree]]
[[B+ Tree]]
[[Indexes]]
[[Cache Locality]]
[[Write Path]]

---

## 10. Interview Questions

- Why do databases use pages instead of rows?
- What is a buffer pool?
- What happens during a page split?

---

## 11. Summary

Page structure is the fundamental disk abstraction used by databases, enabling efficient caching, I/O batching, and predictable storage layout.