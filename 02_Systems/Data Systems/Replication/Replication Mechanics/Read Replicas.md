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

# Read Replicas

Date: 2026-06-27

---

## 1. Problem

Primary databases can become overloaded when serving both reads and writes.

We need a way to scale read traffic independently from write operations.

---

## 2. Intuition

Read replicas are “read-only copies of the primary database.”

They allow read scaling by offloading queries from the primary node.

Think:
- primary handles writes
- replicas handle reads

---

## 3. How It Works

1. Primary processes writes
2. Changes are replicated to read replicas
3. Applications route read queries to replicas
4. Replicas asynchronously apply updates

---

## 4. Key Components

- primary node
- read replicas
- replication stream
- load balancer / query router
- lag monitoring system

---

## 5. Tradeoffs

### Pros
- scalable read throughput
- reduced load on primary
- improved read latency distribution

### Cons
- replication lag causes stale reads
- increased infrastructure cost
- complex routing logic

---

## 6. Scaling / Complexity

Read scaling:

$$
O(n_{replicas})
$$

Write cost remains:

$$
O(1)
$$

but multiplied replication overhead increases backend load.

---

## 7. Real Systems Usage

- PostgreSQL read replicas
- MySQL replication clusters
- cloud databases (AWS RDS, Aurora)
- analytics systems separating OLTP and OLAP

---

## 8. Failure Modes

- stale reads due to lag
- uneven load distribution across replicas
- replica failure reducing read capacity
- inconsistent read routing

Mitigations:
- replica health checks
- consistent hashing for routing
- read-after-write routing to primary
- lag-aware routing

---

## 9. Related Concepts

[[Followers]]
[[Replication Lag]]
[[Log Shipping]]
[[Eventual Consistency]]
[[Strong Consistency]]

---

## 10. Interview Questions

- What are read replicas?
- How do they improve scalability?
- What consistency issues arise?
- How do you route reads correctly?

---

## 11. Summary

Read replicas are asynchronous copies of a primary database used to scale read traffic, but they introduce consistency challenges due to replication lag.