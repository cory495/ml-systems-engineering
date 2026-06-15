# Storage Engines

Date: 2026-06-15

---

## 1. Problem

How can a database efficiently store, retrieve, update, and delete large amounts of data while maintaining acceptable performance?

Without a storage engine, a database would simply be a collection of files with no optimized mechanism for accessing data.

---

## 2. Intuition

A storage engine is the component responsible for managing how data is physically stored and retrieved.

Think of it as the "engine" inside a car.

Users interact with SQL or APIs, but the storage engine determines:

- How data is written
    
- How data is found
    
- How indexes are maintained
    
- How updates are processed
    

Different storage engines optimize for different workloads.

---

## 3. How It Works

- Step 1: Receive a read or write request.
    
- Step 2: Locate relevant indexes.
    
- Step 3: Access data from memory or disk.
    
- Step 4: Return results or persist changes.
    

---

## 4. Key Components

- Data files
    
- Indexes
    
- Cache
    
- Read path
    
- Write path
    
- Compaction (for log-structured systems)
    

---

## 5. Tradeoffs

### Pros

- Efficient data access
    
- Optimized storage
    
- Supports large datasets
    

### Cons

- Different engines favor different workloads
    
- Increased implementation complexity
    

### When NOT to use it

A database always requires some form of storage engine.

The real question is choosing the correct one.

---

## 6. Scaling / Complexity

### Time

Varies by implementation.

Examples:

- B-Tree lookup: O(log n)
    
- Hash lookup: O(1) average
    

### Space

Requires storage for:

- Data
    
- Indexes
    
- Metadata
    

### Bottlenecks

- Disk I/O
    
- Memory pressure
    
- Cache misses
    

---

## 7. Real Systems Usage

### PostgreSQL

B-Tree storage engine.

### MySQL InnoDB

Page-oriented storage engine.

### Cassandra

LSM Tree storage engine.

### RocksDB

LSM Tree storage engine.

### Kafka

Append-only log storage.

---

## 8. Failure Modes

### Disk Failures

Stored data becomes unavailable.

### Corrupted Indexes

Queries fail or return incorrect data.

### Cache Thrashing

Performance collapses due to excessive disk access.

---

## 9. Related Concepts

[[Read Path]]  
[[Write Path]]  
[[Indexes]]  
[[B-Tree]]  
[[LSM Tree]]

---

## 10. Interview Questions

- What is a storage engine?
    
- Why do databases have different storage engines?
    
- How does a storage engine affect performance?
    

---

## 11. Summary

A storage engine determines how data is stored and retrieved. Different storage engines optimize for different workloads, making storage engine selection a critical database design decision.