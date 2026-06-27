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

# Followers

Date: 2026-06-27

---

## 1. Problem

Single-node databases cannot handle high read throughput or provide high availability under failures.

We need additional nodes that replicate data and can take over or serve reads when the primary is under load or unavailable.

---

## 2. Intuition

Followers are “shadow copies” of the primary database.

They continuously replicate changes so they can serve as backups or read scaling nodes.

Think:
- primary = source of truth
- followers = synchronized mirrors

---

## 3. How It Works

1. Primary processes all writes
2. Writes are propagated to follower nodes
3. Followers apply changes in the same order
4. Followers serve read queries or stand by for failover

---

## 4. Key Components

- primary node
- follower replicas
- replication stream
- commit log
- sync mechanism

---

## 5. Tradeoffs

### Pros
- read scalability
- high availability
- isolation of read traffic from writes

### Cons
- replication lag
- stale reads possible
- added system complexity

---

## 6. Scaling / Complexity

Follower scaling:

$$
O(n)
$$

Replication delay depends on pipeline latency:

$$
O(\Delta t)
$$

---

## 7. Real Systems Usage

- PostgreSQL streaming replicas
- MySQL replication setups
- distributed SQL systems
- cloud-managed databases

---

## 8. Failure Modes

- follower lagging behind primary
- follower crash causing replication backlog
- inconsistent reads if routed incorrectly
- failover lag during primary outage

Mitigations:
- health checks
- read routing policies
- replication monitoring
- quorum-based reads

---

## 9. Related Concepts

[[Replication Lag]]
[[Read Replicas]]
[[Write-Ahead Log (WAL)]]
[[Log Shipping]]
[[Strong Consistency]]

---

## 10. Interview Questions

- What is a follower in replication systems?
- How do followers differ from leaders?
- What happens when followers fall behind?
- Can followers serve writes?

---

## 11. Summary

Followers are replica nodes that mirror a primary database’s state, enabling read scaling and fault tolerance, but introducing challenges like replication lag and stale reads.