# B-Tree

Date: 2026-061-5

---

## 1. Problem

How can a database maintain sorted data while supporting efficient lookups, inserts, and range queries?

---

## 2. Intuition

A B-Tree is a self-balancing search tree optimized for disks.

Instead of storing one key per node, each node stores many keys.

This dramatically reduces tree height and minimizes disk accesses.

---

## 3. How It Works

- Step 1: Store multiple keys in each node.
    
- Step 2: Keep keys sorted.
    
- Step 3: Navigate through child pointers.
    
- Step 4: Split nodes when they become full.
    
![[pic_btree.png]]
---

## 4. Key Components

- Root node
    
- Internal nodes
    
- Leaf nodes
    
- Pages
    
- Child pointers
    

---

## 5. Tradeoffs

### Pros

- O(log n) lookup
    
- O(log n) insertion
    
- Efficient range scans
    
- Widely used
    

### Cons

- Random writes
    
- Page splits
    
- More write amplification than append-only systems
    

### When NOT to use it

Write-heavy workloads may benefit from LSM Trees.

---

## 6. Scaling / Complexity

### Search

O(log n)

### Insert

O(log n)

### Space

O(n)

### Bottlenecks

- Disk seeks
    
- Page splits
    
- Cache misses
    

---

## 7. Real Systems Usage

### PostgreSQL

Primary indexing structure.

### MySQL InnoDB

Clustered B-Tree indexes.

### SQLite

B-Tree storage.

---

## 8. Failure Modes

### Frequent Splits

Write performance suffers.

### Poor Cache Locality

Additional disk access required.

### Large Working Sets

Pages continually evicted from memory.

---

## 9. Related Concepts

[[Indexes]]  
[[B+ Tree]]  
[[Range Queries]]  
[[LSM Tree]]

---

## 10. Interview Questions

- Why do databases use B-Trees?
    
- Why not binary search trees?
    
- Why are B-Trees disk friendly?
    
- Compare B-Trees and LSM Trees.
    

---

## 11. Summary

B-Trees are balanced search structures optimized for disk storage. They provide predictable O(log n) performance and efficient range queries, making them one of the most widely used indexing structures in databases.