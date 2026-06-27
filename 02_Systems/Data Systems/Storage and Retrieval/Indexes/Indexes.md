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
# Indexes

Date: 2026-06-15

---

## 1. Problem

How can a database find records efficiently without scanning every row?

A full table scan becomes prohibitively expensive as data grows.

---

## 2. Intuition

An index is similar to a book's table of contents.

Instead of reading every page, you jump directly to the location of the information.

Indexes trade additional storage and write overhead for faster lookups.

---

## 3. How It Works

- Step 1: Build a data structure mapping keys to records.
    
- Step 2: Maintain the structure during writes.
    
- Step 3: Use the structure to locate records during reads.
    

---

## 4. Key Components

- Search key
    
- Record pointer
    
- Data structure
    
- Maintenance logic
    

---

## 5. Tradeoffs

### Pros

- Faster reads
    
- Efficient filtering
    
- Improved query performance
    

### Cons

- Extra storage
    
- Slower writes
    
- Maintenance overhead
    

### When NOT to use it

- Very small tables
    
- Rarely queried columns
    

---

## 6. Scaling / Complexity

### Lookup

Depends on index type.

Examples:

- Hash Index → O(1)
    
- B-Tree → O(log n)
    

### Space

O(n)

### Bottlenecks

- Index maintenance
    
- Memory usage
    
- Disk seeks
    

---

## 7. Real Systems Usage

### PostgreSQL

B-Tree indexes.

### MySQL

Clustered indexes.

### Elasticsearch

Inverted indexes.

### Cassandra

Partition indexes.

---

## 8. Failure Modes

### Too Many Indexes

Write performance degrades.

### Missing Indexes

Queries become full scans.

### Index Fragmentation

Performance decreases over time.

---

## 9. Related Concepts

[[Hash Index]]  
[[Primary Index]]  
[[Secondary Index]]  
[[B-Tree]]  
[[LSM Tree]]

---

## 10. Interview Questions

- Why do indexes improve performance?
    
- What costs do indexes introduce?
    
- Why not index every column?
    

---

## 11. Summary

Indexes accelerate data retrieval by maintaining auxiliary search structures. Faster reads come at the cost of storage and write overhead.