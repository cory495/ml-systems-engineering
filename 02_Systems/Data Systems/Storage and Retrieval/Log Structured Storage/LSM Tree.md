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
# LSM Tree

Date: 2026-06-15

---

## 1. Problem

How can we support fast writes and still maintain efficient reads in a persistent storage system?

B-Trees optimize reads but suffer from random write overhead.

We need a structure optimized for **write-heavy workloads**.

---

## 2. Intuition

An LSM Tree (Log Structured Merge Tree) turns random writes into sequential writes by buffering them in memory and periodically flushing sorted data to disk.

Instead of updating data in place:

> We batch writes, sort them, and merge them later.

---

## 3. How It Works

- Step 1: Writes go to Memtable (in-memory sorted structure)
- Step 2: Writes are appended to WAL for durability
- Step 3: Memtable flushes into SSTables when full
- Step 4: SSTables accumulate over time
- Step 5: Background compaction merges SSTables

---

## 4. Key Components

- Memtable
- Write-ahead log (WAL)
- SSTables
- Compaction process
- Bloom filters (often used for fast negative lookups)

---

## 5. Tradeoffs

### Pros

- Extremely fast writes
- Sequential disk access
- High throughput
- Good for large-scale distributed systems

### Cons

- Read amplification (multiple SSTables checked)
- Write amplification (due to compaction)
- Complex background maintenance
- Higher latency spikes during compaction

---

## 6. Scaling / Complexity

### Write
O(1) amortized (append + flush)

### Read
O(log n) best case, worse with many SSTables

### Bottlenecks
- Compaction overhead
- Read amplification
- Memory pressure from Memtable
- Disk bandwidth during merges

---

## 7. Real Systems Usage

- Cassandra
- RocksDB
- LevelDB
- Bigtable
- HBase
- ScyllaDB
- Dynamo-style systems

---

## 8. Failure Modes

- Compaction backlog → read latency spikes
- SSTable explosion → degraded performance
- Memory pressure in Memtable
- Disk write storms during compaction
- Uneven key distribution causing hotspots

---

## 9. Related Concepts

[[Memtable]]
[[SSTable]]
[[Compaction]]
[[Write Path]]
[[Log Structured Storage]]
[[B-Tree]]

---

## 10. Interview Questions

- Why are LSM trees better for write-heavy workloads?
- What is read amplification?
- What is write amplification?
- How does compaction affect performance?
- Why not just use a B-Tree?

---

## 11. Summary

LSM Trees optimize for write throughput by buffering writes in memory and converting them into sequential disk writes. Reads are more complex due to multiple levels of SSTables, and compaction is required to maintain performance.