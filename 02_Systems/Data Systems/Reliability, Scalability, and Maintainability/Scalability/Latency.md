---
Created: 2026-06-01
Updated: 2026-06-26
tags:
  - systems
  - programming
  - databases
Type: Notes
---
# Latency

Date: 2026-06-15

---

## 1. Problem

How long does a single operation take?

---

## 2. Intuition

Latency measures waiting time.

Users care more about latency than throughput because they directly experience delays.

---

## 3. How It Works

- Request arrives.
- Processing occurs.
- Response returns.

Latency = Response Time - Request Time

---

## 4. Key Components

- Network latency
- Disk latency
- Queueing latency
- Processing latency

---

## 5. Tradeoffs

### Pros
- Reflects user experience
- Easy to understand

### Cons
- Can fluctuate significantly
- Doesn't indicate total system capacity

### When NOT to use it

When evaluating overall workload capacity.

---

## 6. Scaling / Complexity

### Bottlenecks

- Network delays
- Database queries
- Lock contention
- Disk access

---

## 7. Real Systems Usage

- API response times
- Database queries
- Search engines
- LLM inference

---

## 8. Failure Modes

- Queue buildup
- Traffic spikes
- Resource contention

---

## 9. Related Concepts

[[Response Time]]
[[Throughput]]
[[Tail Latency]]
[[Percentile Metrics]]

---

## 10. Interview Questions

- What contributes to latency?
- How can latency be reduced?

---

## 11. Summary

Latency measures the time required for a single operation to complete. Low latency improves user experience.