---
Created: 2026-06-27
Updated: 2026-06-27
tags:
  - systems
  - distributed-systems
  - replication
Type: Notes
---

# Leader-Based Replication

Date: 2026-06-27

---

## 1. Problem

Coordinating writes across multiple replicas is difficult because concurrent updates can lead to inconsistency.

We need a way to define a single authority for ordering writes.

---

## 2. Intuition

Leader-based replication is “one boss, many followers.”

All writes go through a single leader, which defines the global order of operations.

---

## 3. How It Works

1. Client sends write to leader
2. Leader assigns order to write
3. Leader appends write to log
4. Followers replicate log entries
5. Followers apply changes in same order

Reads may be:
- from leader (strong consistency)
- from followers (possibly stale)

---

## 4. Key Components

- leader node
- follower replicas
- replication log
- consensus or leader election system
- failover mechanism

---

## 5. Tradeoffs

### Pros
- strong consistency (when reading from leader)
- simple write ordering
- widely used and well-understood

### Cons
- leader bottleneck
- reduced availability if leader fails
- replication lag on followers

---

## 6. Scaling / Complexity

Write throughput limited by leader:

$$
O(1) \text{ per leader}
$$

Follower scaling improves read throughput but not writes.

---

## 7. Real Systems Usage

- PostgreSQL primary-replica setup
- MySQL replication
- Kafka partitions (leader per partition)
- etcd / ZooKeeper (consensus-based leaders)

---

## 8. Failure Modes

- leader crash causing downtime
- split brain during election
- follower lag
- overload on leader node

Mitigations:
- leader election (Raft/Paxos)
- failover mechanisms
- read replicas
- quorum-based consensus

---

## 9. Related Concepts

[[Replication]]
[[Replication Lag]]
[[Failover]]
[[Quorums]]
[[Strong Consistency]]

---

## 10. Interview Questions

- What is leader-based replication?
- Why does it simplify consistency?
- What happens when the leader fails?
- How does it scale?

---

## 11. Summary

Leader-based replication routes all writes through a single leader to ensure a consistent global order of operations, simplifying correctness at the cost of potential bottlenecks and availability constraints.