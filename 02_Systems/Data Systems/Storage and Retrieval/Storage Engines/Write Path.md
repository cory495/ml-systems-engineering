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
# Write Path

Date: 2026-06-15

---

## 1. Problem

How does a database safely and efficiently persist new data?

Writing directly to disk for every operation can be extremely slow.

---

## 2. Intuition

The write path is the sequence of operations that occur when data is inserted, updated, or deleted.

Different storage engines optimize writes differently.

B-Trees update pages directly.

LSM Trees append writes and reorganize later.

---

## 3. How It Works

General Process:

- Step 1: Receive write request.
- Step 2: Validate transaction.
- Step 3: Record write in a log.
- Step 4: Update in-memory structures.
- Step 5: Persist data to disk.
- Step 6: Acknowledge success.

---

## 4. Key Components

- Write-ahead log (WAL)
- Memtable
- Data pages
- Compaction
- Storage engine

---

## 5. Tradeoffs

### Pros

- Durable persistence
- Crash recovery
- Consistent updates

### Cons

- Write amplification
- Logging overhead
- Synchronization costs

### When NOT to use it

A write path is always required in persistent systems.

---

## 6. Scaling / Complexity

### B-Tree Writes

O(log n)

### LSM Tree Writes

Near O(1) append performance

### Bottlenecks

- Disk bandwidth
- Synchronization
- Compaction
- Lock contention

---

## 7. Real Systems Usage

### PostgreSQL

WAL → B-Tree updates.

### MySQL InnoDB

Redo log → page modification.

### Cassandra

Commit log → memtable.

### RocksDB

WAL → memtable → SSTable.

---

## 8. Failure Modes

### Disk Failure

Writes cannot be persisted.

### WAL Corruption

Recovery becomes difficult.

### Compaction Overload

Write latency spikes.

### Lock Contention

Concurrency decreases.

---

## 9. Related Concepts

[[Read Path]]
[[Storage Engine]]
[[Write Amplification]]
[[Append-Only Logs]]
[[LSM Tree]]

---

## 10. Interview Questions

- Why use a write-ahead log?
- Why are writes expensive?
- Compare B-Tree and LSM Tree write paths.
- What is write amplification?

---

## 11. Summary

The write path governs how data is safely persisted. Modern databases optimize writes using logs, memory buffers, and storage-engine-specific techniques to balance durability and performance.