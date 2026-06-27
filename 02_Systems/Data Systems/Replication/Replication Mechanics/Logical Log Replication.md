---
Created: 2026-06-27
Updated: 2026-06-27
tags:
  - systems
  - databases
  - replication
Type: Notes
---

# Logical Log Replication

Date: 2026-06-27

---

## 1. Problem

Physical replication (page-level or byte-level) can be inefficient and tightly coupled to storage layout.

We need a replication method that captures **meaningful data changes independent of storage format**.

---

## 2. Intuition

Logical log replication sends “what changed” rather than “how it was stored.”

It represents operations like INSERT, UPDATE, DELETE instead of raw disk modifications.

---

## 3. How It Works

1. Primary converts changes into logical operations
2. Log is generated (e.g., row-level changes)
3. Replicas apply logical operations
4. State converges regardless of physical layout

---

## 4. Key Components

- logical change log
- replication stream
- schema metadata
- apply engine on replicas

---

## 5. Tradeoffs

### Pros
- decoupled from storage engine
- more flexible replication across systems
- easier cross-version compatibility

### Cons
- higher CPU overhead
- complex schema evolution handling
- potential lag in transformation layer

---

## 6. Scaling / Complexity

Replication cost:

$$
O(k)
$$

where \(k\) is number of logical operations per transaction.

---

## 7. Real Systems Usage

- PostgreSQL logical replication
- Debezium (CDC systems)
- distributed event streaming pipelines
- data warehouse ingestion systems

---

## 8. Failure Modes

- schema mismatch across replicas
- transformation errors in log parsing
- lag in event pipelines
- missing or reordered events

Mitigations:
- schema registry
- idempotent operations
- versioned event formats
- replay-safe pipelines

---

## 9. Related Concepts

[[Write-Ahead Log (WAL)]]
[[Log Shipping]]
[[Statement-Based Replication]]
[[Replication Lag]]
[[Schema Evolution]]

---

## 10. Interview Questions

- What is logical log replication?
- How does it differ from physical replication?
- Why is it useful for heterogeneous systems?
- What are its failure modes?

---

## 11. Summary

Logical log replication captures high-level data changes instead of physical storage modifications, enabling flexible, cross-system replication at the cost of additional processing complexity.