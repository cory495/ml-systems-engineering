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
# Aggregate-Oriented Design

Date: 2026-06-15

---

## 1. Definition

A modeling approach where related data is stored and managed as a single unit called an aggregate.

---

## 2. Why It Matters

Aggregates reduce joins and align storage with common access patterns.

---

## 3. Key Ideas

- Store related data together
- Optimize for retrieval
- Common in document databases

---

## 4. Examples

Order document:

```json
{
  "order_id": 1,
  "customer": {...},
  "items": [...]
}
```

Entire order retrieved with one query.

---

## 5. How It Is Achieved

Embed related entities inside a parent object.

---

## 6. Tradeoffs

### Pros

- Fast reads
- Fewer joins
- Simpler queries

### Cons

- Data duplication
- Larger records

---

## 7. Related Concepts

- [[Document Models]]
- [[Denormalization]]
- [[NoSQL]]

---

## 8. Summary

Aggregate-oriented design groups related information together to optimize access patterns and reduce query complexity.