---
Created: 2026-06-27
Updated: 2026-06-27
tags:
  - systems
  - databases
  - replication
Type: Concept
---

# Statement-Based Replication

Date: 2026-06-27

---

## 1. Problem

Replicating raw data changes can be expensive and storage-heavy.

We need a compact way to replicate database operations across nodes.

---

## 2. Intuition

Statement-based replication sends the **SQL queries themselves** instead of row-level changes.

Replicas execute the same statements to reach the same state.

---

## 3. How It Works

1. Primary executes SQL statement
2. Statement is logged
3. Statement is sent to replicas
4. Replicas execute identical SQL
5. State converges if execution is deterministic

---

## 4. Key Components

- SQL statement log
- replication coordinator
- replica execution engine
- deterministic execution guarantees

---

## 5. Tradeoffs

### Pros
- compact replication format
- low storage overhead
- simple conceptual model

### Cons
- non-deterministic functions break consistency
- time-dependent queries cause divergence
- harder debugging of replicas

---

## 6. Scaling / Complexity

Replication cost:

$$
O(1)
$$

but correctness depends on deterministic execution.

---

## 7. Real Systems Usage

- MySQL statement-based replication (legacy mode)
- controlled distributed SQL environments
- systems with strict deterministic guarantees

---

## 8. Failure Modes

- divergence due to NOW(), RAND(), etc.
- inconsistent execution order
- hidden side effects in statements
- schema differences across replicas

Mitigations:
- restrict nondeterministic SQL
- use row-based replication instead
- enforce deterministic execution mode

---

## 9. Related Concepts

[[Log Shipping]]
[[Write-Ahead Log (WAL)]]
[[Logical Log Replication]]
[[Replication Lag]]
[[Conflict Resolution]]

---

## 10. Interview Questions

- What is statement-based replication?
- Why can it cause divergence?
- When is it safe to use?
- How does it compare to row-based replication?

---

## 11. Summary

Statement-based replication propagates SQL queries to replicas, offering compact replication but requiring strict determinism to avoid divergence.