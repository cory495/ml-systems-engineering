---
Created: 2026-06-01
Updated: 2026-06-26
tags:
  - systems
  - programming
  - databases
Type: Notes
---
# Tail Latency

Date: 2026-06-15

---

## 1. Problem

How do we measure the slowest requests in a system?

---

## 2. Intuition

Users remember the slowest experiences.

A small number of extremely slow requests can dominate perceived performance.

---

## 3. How It Works

Tail latency focuses on:

- P95
- P99
- P999

instead of averages.

---

## 4. Key Components

- Outlier requests
- Percentiles
- Resource contention
- Queue buildup

---

## 5. Tradeoffs

### Pros
- Captures real-world performance
- Reveals hidden bottlenecks

### Cons
- Harder to optimize
- Requires extensive monitoring

### When NOT to use it

When analyzing tiny workloads.

---

## 6. Scaling / Complexity

Tail latency often worsens as systems become distributed.

---

## 7. Real Systems Usage

- Google Search
- Amazon
- Distributed databases
- LLM serving infrastructure

---

## 8. Failure Modes

- Slow disks
- Garbage collection pauses
- Network congestion
- Hot partitions

---

## 9. Related Concepts

[[Latency]]
[[Percentile Metrics]]
[[Response Time]]

---

## 10. Interview Questions

- Why does tail latency matter?
- How does distribution increase tail latency?

---

## 11. Summary

Tail latency measures the slowest requests in a system and often determines overall user experience.