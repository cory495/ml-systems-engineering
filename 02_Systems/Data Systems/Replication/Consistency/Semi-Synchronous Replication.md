---
Created: 2026-06-27
Updated: 2026-06-27
tags:
  - systems
  - distributed-systems
  - consistency
Type: Notes
---

# Semi-Synchronous Replication

Date: 2026-06-27

---

## 1. Problem

Synchronous replication is too slow, while asynchronous replication risks data loss.

We need a middle ground that balances consistency and performance.

---

## 2. Intuition

Semi-synchronous replication is “wait for at least one replica, not all.”

It ensures durability across multiple nodes without blocking on the slowest replicas.

---

## 3. How It Works

1. Primary receives write
2. Primary writes to local log
3. Primary waits for at least one replica acknowledgment
4. Remaining replicas are updated asynchronously
5. Client is acknowledged after minimum replication guarantee

---

## 4. Key Components

- primary node
- replica set
- acknowledgment quorum (partial)
- replication log
- timeout mechanism

---

## 5. Tradeoffs

### Pros
- lower latency than synchronous replication
- better durability than asynchronous replication
- reduced risk of data loss

### Cons
- still vulnerable to some data loss scenarios
- more complex than async replication
- inconsistent replication timing

---

## 6. Scaling / Complexity

Write latency:

$$
O(R_{min})
$$

where \(R_{min}\) is minimum required replica acknowledgments.

---

## 7. Real Systems Usage

- MySQL semi-sync replication
- cloud-managed relational databases
- distributed systems requiring durability guarantees

---

## 8. Failure Modes

- data loss if acknowledged replica fails before full sync
- replication lag across non-ack replicas
- failover inconsistencies

Mitigations:
- strict replica selection
- hybrid quorum models
- logging and replay mechanisms

---

## 9. Related Concepts

[[Synchronous Replication]]
[[Asynchronous Replication]]
[[Eventual Consistency]]
[[Quorums]]
[[Failover]]

---

## 10. Interview Questions

- What is semi-synchronous replication?
- How does it balance latency and durability?
- What happens if the acknowledging replica fails?
- How is it different from quorum replication?

---

## 11. Summary

Semi-synchronous replication is a hybrid model that requires acknowledgment from at least one replica before confirming writes, balancing performance and durability.