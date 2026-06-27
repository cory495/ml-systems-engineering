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
# Denormalization

Date: 2026-06-15

---

## 1. Definition

Denormalization intentionally duplicates data to improve read performance.

---

## 2. Why It Matters

Modern applications often optimize for reads rather than storage efficiency.

---

## 3. Key Ideas

- Duplicate frequently accessed data
- Reduce joins
- Faster reads
- More expensive writes

---

## 4. Examples

Instead of joining Users and Posts:

Store username directly inside each post document.

---

## 5. How It Is Achieved

- Duplicate values
- Precompute results
- Store aggregates

---

## 6. Tradeoffs

### Pros

- Faster queries
- Simpler reads

### Cons

- Data duplication
- Update complexity
- Risk of inconsistency

---

## 7. Related Concepts

- [[Normalization]]
- [[Document Models]]
- [[Aggregate-Oriented Design]]

---

## 8. Summary

Denormalization trades storage efficiency and consistency for improved read performance.