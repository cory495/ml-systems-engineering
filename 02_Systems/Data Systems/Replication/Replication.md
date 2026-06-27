---
Created: 2026-06-27
Updated: 2026-06-27
tags:
  - systems
  - distributed-systems
  - replication
Type: Notes
---

# Replication

Date: 2026-06-27

---

## 1. Problem

Single machines are not sufficient for modern systems due to failures, high load, and geographic distribution requirements.

We need multiple copies of data to improve reliability, availability, and performance.

---

## 2. Intuition

Replication is “keeping multiple synchronized copies of the same data.”

If one node fails or becomes slow, another can serve the same data.

It is the foundation of fault-tolerant distributed systems.

---

## 3. How It Works

1. Data is written to one or more primary nodes
2. Changes are propagated to replicas
3. Replicas maintain consistency via replication protocol
4. Reads can be served from one or many replicas depending on model

---

## 4. Key Components

- primary / leader node
- follower / replica nodes
- replication protocol
- consistency model
- failure detection system

---

## 5. Tradeoffs

### Pros
- fault tolerance
- high availability
- read scalability
- disaster recovery

### Cons
- replication lag
- consistency complexity
- higher infrastructure cost
- operational overhead

---

## 6. Scaling / Complexity

Replication overhead:

$$
O(n_{replicas})
$$

Write amplification increases with number of replicas.

---

## 7. Real Systems Usage

- databases (PostgreSQL, MySQL, Cassandra)
- distributed storage systems
- caching layers
- global-scale services (CDNs, cloud databases)

---

## 8. Failure Modes

- replica divergence
- stale reads
- split brain
- replication lag accumulation
- failover inconsistencies

Mitigations:
- quorums
- consensus protocols
- read repair
- anti-entropy systems

---

## 9. Related Concepts

[[Replication Goals]]
[[Leader-Based Replication]]
[[Multi-Leader Replication]]
[[Leaderless Replication]]
[[Consistency]]

---

## 10. Interview Questions

- What is replication?
- Why is it used in distributed systems?
- What problems does it introduce?
- How do systems keep replicas consistent?

---

## 11. Summary

Replication is the process of maintaining multiple copies of data across nodes to improve fault tolerance, scalability, and availability, while introducing consistency and coordination challenges.