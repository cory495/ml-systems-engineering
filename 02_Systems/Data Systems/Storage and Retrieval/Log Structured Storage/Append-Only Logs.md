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
# Append-Only Logs

Date: 2026-06-15

---

## 1. Problem

How can data be written efficiently without repeatedly modifying existing files?

Updating data in-place often requires expensive disk seeks and random writes.

---

## 2. Intuition

Instead of modifying existing records, simply append new records to the end of a log.

Think of a notebook where you never erase anything. Every change is written as a new entry.

Example:

```text
SET x = 5
SET y = 10
SET x = 7
```

The latest value of x is determined by reading the most recent entry.

![[pic_append_only_log.png]]

---

## 3. How It Works

- Step 1: Receive write request.
    
- Step 2: Append record to end of log.
    
- Step 3: Update in-memory index.
    
- Step 4: Flush data to disk.
    

---

## 4. Key Components

- Log file
    
- Sequential writes
    
- In-memory index
    
- Log segments
    

---

## 5. Tradeoffs

### Pros

- Extremely fast writes
    
- Sequential disk access
    
- Crash recovery simplicity
    

### Cons

- Log grows indefinitely
    
- Reads may become expensive
    
- Requires cleanup mechanisms
    

### When NOT to use it

When workloads require extremely fast point reads without indexing.

---

## 6. Scaling / Complexity

### Write

O(1)

### Read

O(n) without indexes

### Bottlenecks

- Growing log size
    
- Disk space consumption
    

---

## 7. Real Systems Usage

- Kafka
    
- Redis AOF
    
- Cassandra Commit Log
    
- RocksDB WAL
    

---

## 8. Failure Modes

### Log Corruption

Recent writes may be lost.

### Disk Full

New writes fail.

### Huge Logs

Recovery becomes slow.

---

## 9. Related Concepts

[[SSTable]]  
[[Write Path]]  
[[LSM Tree]]  
[[Compaction]]

---

## 10. Interview Questions

- Why are sequential writes faster?
    
- Why not update records in-place?
    
- How do append-only systems recover from crashes?
    

---

## 11. Summary

Append-only logs improve write performance by avoiding random disk updates. New data is appended sequentially and later reorganized for efficient reads.