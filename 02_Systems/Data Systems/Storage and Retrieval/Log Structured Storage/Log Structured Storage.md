# Log Structured Storage

Date: 2026-06-15

---

## 1. Problem

How can databases achieve high write throughput while avoiding expensive in-place updates on disk?

Traditional update-in-place storage suffers from random I/O, fragmentation, and poor write performance at scale.

---

## 2. Intuition

Instead of updating data where it lives, we **only append new data** and treat storage as a sequence of immutable writes.

Over time, the system reorganizes data in the background.

Think of it as:

> "Never overwrite. Always append. Fix later."

---

## 3. How It Works

- Step 1: Incoming writes are appended to a log
- Step 2: Data is stored in sequential segments
- Step 3: Reads consult in-memory indexes or multiple segments
- Step 4: Background processes clean and reorganize data (compaction)

---

## 4. Key Components

- Append-only log
- Segment files
- Immutable data blocks
- Background compaction
- Indexing layer

---

## 5. Tradeoffs

### Pros

- Extremely fast sequential writes
- Great disk utilization
- Simple write path
- Crash recovery is easy

### Cons

- Reads can be slow without indexing
- Requires compaction
- Storage overhead from duplicates

### When NOT to use it

- Pure read-heavy workloads without caching or indexing
- Systems requiring strict in-place updates

---

## 6. Scaling / Complexity

### Write
O(1) sequential append

### Read
O(n) without indexes, O(log n) with indexing structures

### Bottlenecks
- Compaction cost
- Disk space growth
- Read amplification over time

---

## 7. Real Systems Usage

- Kafka (commit log architecture)
- Cassandra (LSM-based storage)
- RocksDB / LevelDB
- HBase
- Redis AOF mode

---

## 8. Failure Modes

- Log growth becomes unbounded
- Read performance degrades without compaction
- Disk saturation
- Recovery time increases with log size

---

## 9. Related Concepts

[[Append-Only Logs]]
[[SSTable]]
[[Memtable]]
[[LSM Tree]]
[[Compaction]]

---

## 10. Interview Questions

- Why are log-structured systems write efficient?
- What tradeoffs does append-only design introduce?
- How do systems avoid infinite log growth?

---

## 11. Summary

Log-structured storage treats disk as an append-only sequence of writes, enabling high throughput writes at the cost of read complexity and background compaction work.