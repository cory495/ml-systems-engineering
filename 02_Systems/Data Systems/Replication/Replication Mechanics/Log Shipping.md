---
Created: 2026-06-27
Updated: 2026-06-27
tags:
  - systems
  - databases
  - replication
Type: Notes
---

# Log Shipping

Date: 2026-06-27

---

## 1. Problem

Replicas need to stay synchronized with the primary database, but copying full database state is expensive and inefficient.

We need a lightweight way to replicate changes incrementally.

---

## 2. Intuition

Log shipping is “replaying the history of changes.”

Instead of sending full snapshots, the system sends a stream of changes recorded in a log.

---

## 3. How It Works

1. Primary writes all changes to a log (WAL or transaction log)
2. Log entries are shipped to replicas
3. Replicas replay log entries in order
4. Replicas reconstruct the same state as primary

---

## 4. Key Components

- write-ahead log (WAL)
- replication stream
- log receiver on replicas
- replay engine

---

## 5. Tradeoffs

### Pros
- efficient incremental replication
- strong ordering guarantees
- simpler than full snapshots

### Cons
- requires strict log ordering
- replay delay introduces lag
- log storage overhead

---

## 6. Scaling / Complexity

Replication cost per operation:

$$
O(1)
$$

Replay cost:

$$
O(n_{log})
$$

---

## 7. Real Systems Usage

- PostgreSQL WAL shipping
- MySQL binlog replication
- SQL Server replication
- distributed databases

---

## 8. Failure Modes

- log corruption or loss
- replica falling behind log head
- replay inconsistencies
- storage pressure from large logs

Mitigations:
- checkpointing
- log truncation
- replication monitoring
- redundancy in log storage

---

## 9. Related Concepts

[[Write-Ahead Log (WAL)]]
[[Replication Lag]]
[[Followers]]
[[Read Replicas]]
[[Logical Log Replication]]

---

## 10. Interview Questions

- What is log shipping?
- Why is it more efficient than full copying?
- What happens if logs are lost?
- How do replicas apply logs?

---

## 11. Summary

Log shipping is a replication technique where changes are transmitted as ordered log entries and replayed on replicas to maintain synchronization efficiently.