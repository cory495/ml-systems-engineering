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
# SSTable

Date: 2026-06-15

---

## 1. Problem

How can append-only logs support efficient lookups?

A giant log is fast to write but slow to search.

---

## 2. Intuition

An SSTable (Sorted String Table) is an immutable file containing sorted key-value pairs.

Because keys are sorted, binary search can quickly locate data.

Example:

```text
A → 1
B → 2
C → 3
D → 4
```

Instead of scanning every record, the database can jump directly to the desired key.

---

## 3. How It Works

- Step 1: Collect writes in memory.
    
- Step 2: Sort keys.
    
- Step 3: Write sorted records to disk.
    
- Step 4: Never modify the file again.
    
![[pic_ssttable.png]]
---

## 4. Key Components

- Sorted keys
    
- Immutable files
    
- Sparse indexes
    
- Block structure
    

---

## 5. Tradeoffs

### Pros

- Efficient lookups
    
- Efficient range scans
    
- Simplifies concurrency
    

### Cons

- Immutable
    
- Creates duplicate versions of records
    
- Requires compaction
    

### When NOT to use it

When frequent in-place updates are required.

---

## 6. Scaling / Complexity

### Search

O(log n)

### Write

Sequential write

### Bottlenecks

- Many SSTables
    
- Compaction overhead
    

---

## 7. Real Systems Usage

- Cassandra
    
- RocksDB
    
- LevelDB
    
- ScyllaDB
    
- Bigtable
    

---

## 8. Failure Modes

### Too Many SSTables

Reads become slower.

### Compaction Backlog

Performance deteriorates.

### Storage Growth

Duplicate records accumulate.

---

## 9. Related Concepts

[[Memtable]]  
[[LSM Tree]]  
[[Compaction]]  
[[Sparse Index]]

---

## 10. Interview Questions

- Why must SSTables remain sorted?
    
- Why are SSTables immutable?
    
- How do SSTables enable fast reads?
    

---

## 11. Summary

SSTables store sorted immutable key-value data. They provide fast reads while maintaining the write advantages of append-only storage.