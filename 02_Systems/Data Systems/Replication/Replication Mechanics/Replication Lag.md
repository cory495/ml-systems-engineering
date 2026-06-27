---
Created: 2026-06-27
Updated: 2026-06-27
tags:
  - systems
  - databases
  - replication
Type: Concept
---

# Replication Lag

Date: 2026-06-27

---

## 1. Problem

In replicated systems, updates from the primary node take time to reach follower nodes.

This delay causes inconsistencies between what the primary has committed and what replicas can serve.

---

## 2. Intuition

Replication lag is “the delay between truth and copies catching up.”

The system is temporarily inconsistent because replicas are always slightly behind the primary.

---

## 3. How It Works

1. Primary commits a write
2. Write enters replication pipeline (log shipping or streaming)
3. Followers apply updates asynchronously
4. Time gap between steps creates lag

---

## 4. Key Components

- replication queue
- network transport layer
- follower apply process
- commit log

---

## 5. Tradeoffs

### Pros
- enables high throughput writes
- decouples primary from replicas
- improves scalability

### Cons
- stale reads
- inconsistent query results across replicas
- unpredictable freshness

---

## 6. Scaling / Complexity

Lag is:

$$
\Delta t = t_{replica} - t_{primary}
$$

Worst-case lag increases under:
- high write load
- slow network
- slow follower disk I/O

---

## 7. Real Systems Usage

- PostgreSQL streaming replication
- MySQL replicas
- Cassandra eventual consistency systems
- Kafka consumer lag analog

---

## 8. Failure Modes

- read-after-write violations
- stale dashboards or analytics
- replica falling permanently behind
- cascading failover to stale node

Mitigations:
- read-your-writes consistency
- synchronous replication options
- monitoring replication delay
- adaptive backpressure

---

## 9. Related Concepts

[[Followers]]
[[Read Replicas]]
[[Eventual Consistency]]
[[Log Shipping]]
[[Write-Ahead Log (WAL)]]

---

## 10. Interview Questions

- What is replication lag?
- Why does it occur?
- How does it affect consistency?
- How can systems reduce it?

---

## 11. Summary

Replication lag is the delay between writes on a primary and their application on replicas, creating temporary inconsistency but enabling scalable asynchronous replication systems.