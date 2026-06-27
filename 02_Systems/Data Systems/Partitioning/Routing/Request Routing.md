---
Created: 2026-06-27
Updated: 2026-06-27
tags:
  - systems
  - distributed-systems
  - routing
Type: Notes
---

# Request Routing

Date: 2026-06-27

---

## 1. Problem

In distributed systems, incoming requests must be directed to the correct backend instance.

The system must decide:
- which shard owns the data
- which replica should serve reads/writes
- how to handle failures and retries

Without request routing, clients would need full system awareness, making scaling impossible.

---

## 2. Intuition

Request routing is the decision-making process that maps a request → a destination node.

It is the operational layer that turns abstract data ownership rules into concrete network calls.

Think of it as:
> “Given this request, who should handle it right now?”

---

## 3. How It Works

Typical flow:

1. Request arrives at gateway / service entry point
2. Extract routing key (user ID, shard key, etc.)
3. Compute destination using:
   - hash-based routing
   - range-based routing
   - directory lookup
4. Forward request to target node
5. Retry or redirect if node is unhealthy

---

## 4. Key Components

- Routing key extractor
- Partitioning function (hash/range)
- Routing table / metadata
- Load balancer integration
- Retry policy / fallback routing

---

## 5. Tradeoffs

### Pros
- abstracts distributed complexity
- enables horizontal scaling
- improves fault isolation

### Cons
- routing logic can become complex
- stale routing tables cause errors
- added latency per request

---

## 6. Scaling / Complexity

Routing decision:

$$
O(1)
$$

Metadata lookup:

$$
O(1) \text{ to } O(\log n)
$$

Bottlenecks:
- centralized routing services
- cache invalidation delays
- high QPS metadata access

---

## 7. Real Systems Usage

- Distributed databases (sharded SQL, NoSQL systems)
- API gateways
- Microservice platforms
- CDN edge routing
- LLM inference routers (model / shard selection)

---

## 8. Failure Modes

- routing to wrong shard due to stale metadata
- uneven load distribution (hot partitions)
- retry storms during partial outages
- infinite redirect loops in misconfigured routing graphs

Mitigations:
- consistent hashing
- bounded retries
- circuit breakers
- versioned routing configs

---

## 9. Related Concepts

[[Routing Layer]]
[[Metadata Service]]
[[Scatter Queries]]
[[Partitioning]]
[[Consistent Hashing]]

---

## 10. Interview Questions

- How does request routing differ from load balancing?
- What causes hot partitions?
- How do systems handle routing during node failure?
- What is consistent hashing and why is it used?

---

## 11. Summary

Request routing is the mechanism that maps incoming requests to the correct backend nodes in a distributed system. It is central to scalability, availability, and performance, but must handle dynamic cluster changes, failures, and uneven load.