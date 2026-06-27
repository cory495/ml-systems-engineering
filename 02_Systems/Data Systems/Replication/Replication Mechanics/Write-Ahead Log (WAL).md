---
Created: 2026-06-27
Updated: 2026-06-27
tags:
  - systems
  - databases
  - replication
  - distributed-systems
Type: Notes
---

# Write-Ahead Log (WAL)

Date: 2026-06-27

---

## 1. Problem

Databases must ensure durability even in the event of crashes or power failures.

We need a mechanism to guarantee that committed changes are not lost.

---

## 2. Intuition

Write-Ahead Logging means “log first, then apply.”

Before modifying actual data pages, the system records the change in a persistent log.

If the system crashes, it can replay the log to recover state.

---

## 3. How It Works

1. Transaction begins
2. Changes are written to WAL
3. WAL is flushed to disk
4. Data pages are updated
5. On crash, WAL is replayed to recover state

---

## 4. Key Components

- WAL file
- transaction log
- checkpoint system
- recovery engine
- buffer pool manager

---

## 5. Tradeoffs

### Pros
- strong durability guarantees
- efficient sequential writes
- enables crash recovery

### Cons
- additional write overhead
- log management complexity
- recovery time after crash

---

## 6. Scaling / Complexity

Write cost:

$$
O(1)
$$

Recovery cost:

$$
O(n_{log})
$$

---

## 7. Real Systems Usage

- PostgreSQL
- MySQL InnoDB
- distributed databases
- log-structured storage systems

---

## 8. Failure Modes

- log corruption
- incomplete flushing before crash
- long recovery times
- disk bottlenecks

Mitigations:
- fsync guarantees
- log segmentation
- checkpoints
- replication of WAL

---

## 9. Related Concepts

[[Log Shipping]]
[[Followers]]
[[Replication Lag]]
[[Statement-Based Replication]]
[[Logical Log Replication]]

---

## 10. Interview Questions

- What is WAL?
- Why is it written before data pages?
- How does it enable crash recovery?
- What are its performance costs?

---

## 11. Summary

Write-Ahead Logging ensures durability by persisting changes in an append-only log before applying them to data pages, enabling reliable recovery after failures.