---
Created: 2026-06-01
Updated: 2026-06-26
tags:
  - systems
  - programming
  - databases
Type: Notes
---
# Joins

Date: 2026-06-15

---

## 1. Definition

A join combines records from multiple tables based on relationships between them.

---

## 2. Why It Matters

Normalization separates data. Joins reconstruct relationships when querying.

---

## 3. Key Ideas

- Combine tables
- Match keys
- Reconstruct entities

---

## 4. Examples

Users:

```sql
UserID | Name
```

Orders:

```sql
OrderID | UserID
```

Join:

```sql
SELECT *
FROM Users
JOIN Orders
ON Users.UserID = Orders.UserID;
```

---

## 5. How It Is Achieved

Database engines:

- Locate matching keys
- Merge records
- Return combined results

---

## 6. Tradeoffs

### Pros

- Flexible relationships
- Strong normalization support

### Cons

- Expensive at scale
- Increased query complexity

---

## 7. Related Concepts

- [[Normalization]]
- [[Denormalization]]
- [[Relational Models]]

---

## 8. Summary

Joins reconstruct relationships across tables and are a foundational operation in relational databases.