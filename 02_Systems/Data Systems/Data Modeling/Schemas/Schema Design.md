---
Created: 2026-06-01
Updated: 2026-06-26
tags:
  - systems
  - programming
  - databases
Type: Notes
---
# Schema Design

Date: 2026-06-15

---

## 1. Problem

How should data be structured so that it supports both efficient storage and efficient querying?

Different workloads require different schema strategies.

---

## 2. Intuition

Schema design is a tradeoff between:

- Write performance
- Read performance
- Flexibility
- Storage efficiency

No single schema fits all systems.

---

## 3. Key Approaches

- Schema-on-write (OLTP)
- Schema-on-read (OLAP)
- Normalization
- Denormalization
- Star schemas

---

## 4. Tradeoffs

- Normalization → reduces redundancy, improves consistency
- Denormalization → improves read performance, increases duplication

---

## 5. Related Concepts

[[OLTP vs OLAP]]
[[Column-Oriented Storage]]
[[Data Warehousing]]
[[Normalization]]
[[Denormalization]]

---

## 6. Summary

Schema design determines how data is structured and heavily influences system performance, consistency, and scalability.