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
# Compression in Column Stores

Date: 2026-06-15

---

## 1. Problem

How do we reduce disk usage and I/O cost when scanning large datasets?

Disk I/O is often the bottleneck in analytical queries.

---

## 2. Intuition

Column stores compress data extremely well because:

- Same data type per column
- High repetition
- Predictable patterns

Compression reduces:
> storage size AND effective I/O per query

---

## 3. How It Works

- Step 1: Split data into columns
- Step 2: Apply compression per column
- Step 3: Store compressed blocks on disk
- Step 4: Decompress only required columns during query

---

## 4. Key Components

- Column chunks
- Compression codecs (Snappy, ZSTD, LZ4)
- Block-level compression
- Metadata for decoding

---

## 5. Tradeoffs

### Pros
- Massive storage reduction
- Faster scans due to reduced I/O
- Better cache efficiency

### Cons
- CPU overhead for decompression
- Random access becomes harder
- Requires block alignment

---

## 6. Real Systems Usage

- Parquet (Snappy/ZSTD)
- ORC
- Snowflake storage engine
- BigQuery storage layer

---

## 7. Summary

Compression in column stores reduces I/O cost by encoding repetitive column data into compact formats optimized for analytical workloads.