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
# Compaction

Date: 2026-06-15

---

## 1. Problem

How do we prevent log-structured systems from growing indefinitely and becoming slow?

Without cleanup, SSTables accumulate duplicate and outdated data.

---

## 2. Intuition

Compaction is the process of merging multiple sorted files into fewer, cleaner files.

During this process:

- Old versions of data are discarded
- Duplicate keys are resolved
- Storage is reorganized for faster reads

Think of it as:

> “Garbage collection for SSTables”

---

## 3. How It Works

- Step 1: Select multiple SSTables
- Step 2: Merge them in sorted order
- Step 3: Keep only latest version of each key
- Step 4: Write new compacted SSTable
- Step 5: Delete old files

---

## 4. Key Components

- SSTables
- Merge process
- Key versioning (timestamps or sequence numbers)
- Background compaction threads

---

## 5. Tradeoffs

### Pros

- Reduces storage overhead
- Improves read performance
- Removes stale data
- Maintains sorted structure

### Cons

- Expensive CPU + I/O operation
- Can cause write amplification
- Can spike latency during execution

### When NOT to use it

You cannot avoid compaction in LSM systems—it is essential.

---

## 6. Scaling / Complexity

### Time

O(n) merge of involved SSTables

### Space

Requires temporary storage during merge

### Bottlenecks

- Disk bandwidth
- CPU usage during merges
- Write amplification

---

## 7. Real Systems Usage

- RocksDB compaction tiers
- Cassandra compaction strategies
- LevelDB background compaction
- Bigtable tablet compaction

---

## 8. Failure Modes

- Compaction backlog → system slowdown
- Too many SSTables → read amplification
- Disk saturation during merges
- Uneven compaction leading to hotspots
- Latency spikes during compaction cycles

---

## 9. Related Concepts

[[LSM Tree]]
[[SSTable]]
[[Memtable]]
[[Write Amplification]]
[[Read Amplification]]

---

## 10. Interview Questions

- Why is compaction necessary?
- What happens if compaction falls behind?
- How does compaction improve reads?
- What is the cost of compaction?

---

## 11. Summary

Compaction merges and cleans SSTables in log-structured systems, removing stale data and reducing read amplification at the cost of additional background write and compute overhead.