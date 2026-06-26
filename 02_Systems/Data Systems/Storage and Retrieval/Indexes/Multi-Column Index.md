---
Created: 2026-06-01
Updated: 2026-06-26
tags:
  - systems
  - programming
  - databases
Type: Notes
---
# Multi-Column Index

Date: 2026-06-15

---

## 1. Problem

How do we efficiently query data using **multiple columns at once**?

Example queries:

- `WHERE last_name = 'Smith' AND first_name = 'John'`
- `WHERE user_id = ? AND timestamp > ?`
- `WHERE country = 'US' AND age > 30`

Single-column indexes are often insufficient or inefficient for these patterns.

---

## 2. Intuition

A multi-column index stores keys composed of **multiple fields combined together**.

Instead of indexing just one column:

```
(last_name)
```

We index a tuple:

```
(last_name, first_name)
```

Think of it as:

> “Sorting by multiple dimensions at once.”

The order of columns matters because the index is lexicographically sorted.

---

## 3. How It Works

- Step 1: Choose column order (this is critical)
- Step 2: Combine columns into a composite key
- Step 3: Build B-Tree (or similar structure) on composite key
- Step 4: Query uses left-to-right prefix matching

Example index:

```
INDEX(last_name, first_name)
```

Supports:

- `WHERE last_name = 'Smith'`
- `WHERE last_name = 'Smith' AND first_name = 'John'`

But NOT efficiently:

- `WHERE first_name = 'John'` (no left prefix match)

---

## 4. Key Components

- Composite key (tuple of columns)
- Lexicographic ordering
- B-Tree or similar index structure
- Column order definition (critical design choice)

---

## 5. Tradeoffs

### Pros
- Efficient multi-column filtering
- Reduces need for multiple indexes
- Supports range + equality combinations

### Cons
- Column order is rigid
- Cannot always reuse for arbitrary filters
- Larger index size than single-column indexes

### When NOT to use it
- Query patterns are highly variable
- Low-selectivity columns dominate
- You cannot predict filter patterns

---

## 6. Scaling / Complexity

### Lookup
O(log n)

### Space
O(n)

### Performance factors
- Column ordering
- Selectivity of leading column
- Cardinality distribution

---

## 7. Real Systems Usage

- PostgreSQL composite B-Tree indexes
- MySQL multi-column indexes (InnoDB)
- ClickHouse sort keys
- BigQuery clustering fields

---

## 8. Failure Modes

- Wrong column order → index becomes useless
- Skipping leftmost column → index not used
- High cardinality mismatch → poor filtering
- Index bloat from too many combinations

---

## 9. Related Concepts

[[Indexes]]
[[Primary Index]]
[[Secondary Index]]
[[B-Tree]]
[[B+ Tree]]
[[Range Queries]]
[[Dense Index]]

---

## 10. Interview Questions

- Why does column order matter in multi-column indexes?
- What is the “leftmost prefix rule”?
- When would a multi-column index not be used?
- How would you design indexes for a query pattern?

---

## 11. Summary

Multi-column indexes store sorted composite keys across multiple columns, enabling efficient filtering across combined attributes, but only when queries respect the index’s column order.