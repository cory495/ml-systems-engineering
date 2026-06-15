# Read Path

Date: 2026-06-15

---

## 1. Problem

How does a database efficiently retrieve requested data?

Without an optimized read path, every query would require scanning the entire dataset.

---

## 2. Intuition

The read path is the sequence of operations that occur when a user requests data.

The goal is to locate data using the fewest possible disk accesses.

Most database optimizations exist to improve the read path.

---

## 3. How It Works

- Step 1: Receive query.
- Step 2: Query planner determines execution strategy.
- Step 3: Locate relevant index.
- Step 4: Search index structure.
- Step 5: Load data from cache or disk.
- Step 6: Return results.

---

## 4. Key Components

- Query planner
- Buffer cache
- Indexes
- Storage engine
- Data pages

---

## 5. Tradeoffs

### Pros

- Fast lookups
- Efficient data retrieval
- Reduced disk access

### Cons

- Additional storage for indexes
- Increased memory requirements

### When NOT to use it

Read optimization is unnecessary for purely write-heavy systems.

---

## 6. Scaling / Complexity

### B-Tree Lookup

O(log n)

### Hash Index Lookup

O(1) average

### Full Table Scan

O(n)

### Bottlenecks

- Disk seeks
- Cache misses
- Network latency

---

## 7. Real Systems Usage

### PostgreSQL

Index scan → page lookup.

### Cassandra

Memtable → SSTables.

### Elasticsearch

Inverted index retrieval.

### Redis

Memory-based lookups.

---

## 8. Failure Modes

### Cache Misses

Reads become disk-bound.

### Missing Indexes

Queries become table scans.

### Fragmented Storage

Additional I/O required.

---

## 9. Related Concepts

[[Write Path]]
[[Indexes]]
[[B-Tree]]
[[LSM Tree]]
[[Cache Locality]]

---

## 10. Interview Questions

- What happens when a query is executed?
- Why are indexes important for reads?
- What causes slow queries?

---

## 11. Summary

The read path describes how data moves from storage to users. Efficient read paths minimize disk access and leverage indexes and caching to improve performance.