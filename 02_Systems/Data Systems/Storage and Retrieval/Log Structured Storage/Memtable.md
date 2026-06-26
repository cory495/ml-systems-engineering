---
Created: 2026-06-01
Updated: 2026-06-26
tags:
  - systems
  - programming
  - databases
Type: Notes
---
# Memtable

Date: 2026-06-15

---

## 1. Problem

How can databases avoid sorting and writing to disk on every update?

Direct disk writes are expensive.

---

## 2. Intuition

A Memtable is an in-memory sorted data structure that temporarily stores writes.

Think of it as a staging area before data is written to disk.

When full, the Memtable is flushed as an SSTable.

---

## 3. How It Works

- Step 1: Write arrives.
    
- Step 2: Insert into Memtable.
    
- Step 3: Append to write-ahead log.
    
- Step 4: Memtable fills.
    
- Step 5: Flush to SSTable.
    

---

## 4. Key Components

- Balanced tree
    
- Skip list
    
- Write-ahead log
    
- Flush mechanism
    

---

## 5. Tradeoffs

### Pros

- Very fast writes
    
- Reduced disk activity
    
- Efficient batching
    

### Cons

- Memory consumption
    
- Requires flushing
    
- Recovery complexity
    

### When NOT to use it

Memory-constrained environments.

---

## 6. Scaling / Complexity

### Insert

O(log n)

### Flush

O(n)

### Bottlenecks

- Memory limits
    
- Flush frequency
    

---

## 7. Real Systems Usage

- Cassandra
    
- RocksDB
    
- LevelDB
    
- ScyllaDB
    

---

## 8. Failure Modes

### Memory Exhaustion

Writes stall.

### Slow Flushes

Latency spikes.

### WAL Failure

Data loss risk.

---

## 9. Related Concepts

[[SSTable]]  
[[LSM Tree]]  
[[Write Path]]  
[[Compaction]]

---

## 10. Interview Questions

- Why not write directly to SSTables?
    
- Why maintain a Memtable?
    
- How does a Memtable improve throughput?
    

---

## 11. Summary

The Memtable buffers writes in memory and periodically flushes them to immutable SSTables, greatly improving write performance.