# Column-Oriented Storage

Date: 2026-06-15

---

## 1. Problem

How can we efficiently run analytical queries over large datasets when most queries only access a subset of columns?

Row storage forces reading entire records even when only a few fields are needed.

---

## 2. Intuition

Instead of storing data row-by-row, store it column-by-column.

So instead of:

```
(row1: A1, B1, C1)
(row2: A2, B2, C2)
```

We store:

```
A: A1, A2
B: B1, B2
C: C1, C2
```

This allows reading only relevant columns.

---

## 3. How It Works

- Step 1: Split table into columns
- Step 2: Store each column separately
- Step 3: Query only required columns
- Step 4: Reconstruct rows during query execution

---

## 4. Key Components

- Column segments
- Compression (very important)
- Vectorized execution
- Block-based storage

---

## 5. Tradeoffs

### Pros
- Extremely fast analytical queries
- High compression ratios
- Reduced I/O
- Cache-friendly for aggregates

### Cons
- Slow single-row lookups
- Complex writes (reconstruction needed)
- Not ideal for OLTP workloads

---

## 6. Scaling / Complexity

### Reads
- Reads only required columns → reduced I/O

### Writes
- More expensive than row storage

### Bottlenecks
- Row reconstruction overhead
- Write amplification
- Column alignment costs

---

## 7. Real Systems Usage

- BigQuery
- Snowflake
- Redshift
- ClickHouse
- Parquet / ORC formats

---

## 8. Failure Modes

- Poor compression strategy → performance loss
- Too many small files → metadata overhead
- Misaligned column chunks → slow reads

---

## 9. Related Concepts

[[OLAP]]
[[Data Warehousing]]
[[Schema-on-Read]]
[[Compression in Column Stores]]
[[Vectorized Execution]]

---

## 10. Summary

Column-oriented storage improves analytical query performance by storing data by column instead of row, drastically reducing I/O for aggregation-heavy workloads.