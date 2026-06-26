---
Created: 2026-06-01
Updated: 2026-06-26
tags:
  - systems
  - programming
  - databases
Type: Notes
---
# Load Parameters

Date: 2026-06-15

---

## 1. Problem

How do we measure the demand placed on a system?

Before scaling a system, we must understand what kind of load it experiences. Different systems become bottlenecked by different factors.

---

## 2. Intuition

A web server may care about requests per second.

A database may care about transactions per second.

A streaming platform may care about concurrent viewers.

A system cannot be scaled effectively without first identifying the correct load parameter.

---

## 3. How It Works

- Step 1: Identify the system's primary workload.
- Step 2: Measure the load being generated.
- Step 3: Track how performance changes as load increases.
- Step 4: Scale resources to handle expected growth.

---

## 4. Key Components

- Requests per second (RPS)
- Concurrent users
- Transactions per second (TPS)
- Messages per second
- Data volume

---

## 5. Tradeoffs

### Pros
- Enables capacity planning
- Helps identify bottlenecks
- Guides scaling decisions

### Cons
- Wrong metrics lead to poor decisions
- Multiple load parameters may exist simultaneously

### When NOT to use it

Never rely on a single load parameter when multiple resources are constrained.

---

## 6. Scaling / Complexity

### Time
O(Load)

### Space
Depends on workload type.

### Bottlenecks
- CPU
- Memory
- Disk I/O
- Network bandwidth

---

## 7. Real Systems Usage

- PostgreSQL: Transactions/sec
- Kafka: Messages/sec
- Redis: Operations/sec
- YouTube: Concurrent streams
- LLM Serving: Tokens/sec

---

## 8. Failure Modes

- Misidentifying bottlenecks
- Scaling wrong resources
- Ignoring traffic spikes

---

## 9. Related Concepts

[[Scalability]]
[[Throughput]]
[[Latency]]
[[Performance]]

---

## 10. Interview Questions

- What load parameters matter for a social network?
- How do load parameters affect scaling decisions?
- Can a system have multiple load parameters?

---

## 11. Summary

Load parameters describe the demand placed on a system. They determine how scalability is measured and guide capacity planning.