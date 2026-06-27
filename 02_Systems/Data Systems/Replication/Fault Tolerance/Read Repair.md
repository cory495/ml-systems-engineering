---
Created: 2026-06-27
Updated: 2026-06-27
tags:
  - systems
  - distributed-systems
  - fault-tolerance
Type: Notes
---

# Read Repair

Date: 2026-06-27

---

## 1. Problem

In eventually consistent systems, replicas may diverge due to delayed replication or temporary failures.

We need a mechanism to detect and correct inconsistencies during normal read operations.

---

## 2. Intuition

Read repair is “fixing data while reading it.”

Instead of waiting for background repair jobs, the system uses reads as an opportunity to synchronize replicas.

---

## 3. How It Works

1. A read request is sent to multiple replicas
2. Responses are compared
3. If inconsistencies are detected:
   - newest version is identified (timestamp/version)
   - outdated replicas are updated
4. Correct value is returned to client

---

## 4. Key Components

- replica comparison logic
- versioning system (timestamps / vector clocks)
- coordinator node
- repair write mechanism

---

## 5. Tradeoffs

### Pros
- improves eventual consistency
- no dedicated repair infrastructure needed
- self-healing behavior

### Cons
- increases read latency
- adds write amplification during reads
- inconsistent repair timing

---

## 6. Scaling / Complexity

Read cost:

$$
O(R)
$$

Repair cost (amortized):

$$
O(R + k)
$$

where \(k\) is number of inconsistent replicas.

---

## 7. Real Systems Usage

- Cassandra
- Dynamo-style systems
- distributed key-value stores
- eventually consistent databases

---

## 8. Failure Modes

- inconsistent timestamp resolution
- read amplification during hot keys
- incomplete repair if quorum not met
- stale replicas persisting under low read traffic

Mitigations:
- periodic anti-entropy processes
- quorum reads
- version vectors

---

## 9. Related Concepts

[[Quorums]]
[[Anti-Entropy]]
[[Conflict Resolution]]
[[Network Partitions]]
[[CAP Theorem]]

---

## 10. Interview Questions

- What is read repair?
- When does it trigger?
- How does it interact with quorums?
- What are its limitations?

---

## 11. Summary

Read repair is a consistency mechanism where inconsistencies between replicas are detected and corrected during read operations, improving eventual consistency at the cost of higher read latency.