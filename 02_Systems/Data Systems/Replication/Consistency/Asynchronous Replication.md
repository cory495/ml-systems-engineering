---
Created: 2026-06-27
Updated: 2026-06-27
tags:
  - systems
  - distributed-systems
  - consistency
Type: Notes
---

# Asynchronous Replication

Date: 2026-06-27

---

## 1. Problem

Synchronous replication introduces high latency because writes must wait for all replicas to acknowledge.

We need a replication model that prioritizes performance and availability over immediate consistency.

---

## 2. Intuition

Asynchronous replication is “acknowledge first, propagate later.”

The system confirms writes quickly and updates replicas in the background.

---

## 3. How It Works

1. Client sends write to primary
2. Primary commits write locally
3. Primary immediately acknowledges client
4. Replicas are updated asynchronously via log shipping or replication stream

---

## 4. Key Components

- primary node
- replication log / WAL
- replication queue
- background sync process

---

## 5. Tradeoffs

### Pros
- low write latency
- high availability
- good throughput

### Cons
- risk of data loss on primary failure
- temporary inconsistency across replicas
- stale reads possible

---

## 6. Scaling / Complexity

Write latency:

$$
O(1)
$$

Replication lag:

$$
O(\Delta t)
$$

where \( \Delta t \) is network and processing delay.

---

## 7. Real Systems Usage

- MySQL async replication
- PostgreSQL streaming replication (async mode)
- Dynamo-style systems
- event streaming architectures

---

## 8. Failure Modes

- data loss if primary crashes before replication
- replica lag causing stale reads
- replication backlog under high load

Mitigations:
- write-ahead logs
- semi-sync replication
- failover strategies with log replay

---

## 9. Related Concepts

[[Synchronous Replication]]
[[Semi-Synchronous Replication]]
[[Eventual Consistency]]
[[Failover]]
[[Replication Log]]

---

## 10. Interview Questions

- What is asynchronous replication?
- Why is it faster than synchronous replication?
- What are the risks of data loss?
- How do systems mitigate replication lag?

---

## 11. Summary

Asynchronous replication prioritizes performance by acknowledging writes immediately and replicating changes in the background, introducing eventual consistency and potential data loss risks.