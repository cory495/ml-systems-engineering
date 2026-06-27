---
Created: 2026-06-27
Updated: 2026-06-27
tags:
  - systems
  - distributed-systems
  - query-processing
Type: Notes
---

# Scatter/Gather Queries

Date: 2026-06-27

---

## 1. Problem

Some queries cannot be answered by a single node because data is partitioned across multiple shards.

We need a mechanism to:
- send a query to many nodes
- collect partial results
- merge them into a final answer

---

## 2. Intuition

Scatter/gather is a distributed search strategy:

- **Scatter:** send request to all relevant nodes
- **Gather:** collect and aggregate responses

It trades efficiency for completeness.

---

## 3. How It Works

1. Client sends query to coordinator
2. Coordinator scatters query to all shards (or subset)
3. Each shard processes query locally
4. Results are returned to coordinator
5. Coordinator aggregates results (merge, sort, reduce)

---

## 4. Key Components

- Coordinator node
- Shard workers
- Fan-out mechanism
- Aggregation logic
- Timeout / partial response handling

---

## 5. Tradeoffs

### Pros
- simple parallelization model
- ensures completeness across shards
- scalable read pattern for distributed systems

### Cons
- high latency (slowest shard dominates)
- expensive network fan-out
- vulnerable to straggler nodes

---

## 6. Scaling / Complexity

Let \(N\) be number of shards:

Latency:

$$
O(\max(T_i))
$$

Work:

$$
O(N)
$$

---

## 7. Real Systems Usage

- distributed search engines (Elasticsearch)
- distributed SQL engines (Presto, Trino)
- logging systems (Splunk-like architectures)
- LLM retrieval systems (multi-index search)

---

## 8. Failure Modes

- straggler nodes increasing tail latency
- partial failure leading to incomplete results
- inconsistent shard state
- network congestion from fan-out storms

Mitigations:
- request hedging
- timeout thresholds
- partial result acceptance
- caching frequent queries

---

## 9. Related Concepts

[[Request Routing]]
[[Routing Layer]]
[[Metadata Service]]
[[Partitioning]]
[[MapReduce]]

---

## 10. Interview Questions

- Why use scatter/gather instead of targeted routing?
- What is the main latency bottleneck?
- How do you handle slow shards?
- How does this relate to MapReduce?

---

## 11. Summary

Scatter/gather queries distribute work across multiple shards and aggregate results centrally. They enable full-system queries in partitioned systems but suffer from high latency and straggler sensitivity.