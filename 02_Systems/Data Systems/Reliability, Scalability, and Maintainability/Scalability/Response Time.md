---
Created: 2026-06-01
Updated: 2026-06-26
tags:
  - systems
  - programming
  - databases
  - distributed-systems
Type: Notes
---
# Response Time

Date: 2026-06-15

---

## 1. Problem

How long does a user wait for a response?

---

## 2. Intuition

Response time is the total delay between a request and a completed response.

From the user's perspective, latency and response time are often interchangeable.

---

## 3. How It Works

Response Time =
Network Delay +
Queue Delay +
Processing Time +
Return Time

---

## 4. Key Components

- Network latency
- Queueing delay
- Service time
- Processing overhead

---

## 5. Tradeoffs

### Pros
- Directly reflects user experience

### Cons
- Difficult to diagnose root causes

### When NOT to use it

When capacity planning is the primary concern.

---

## 6. Scaling / Complexity

### Bottlenecks

- Congestion
- Resource contention
- Slow storage

---

## 7. Real Systems Usage

- REST APIs
- Search engines
- Distributed databases

---

## 8. Failure Modes

- Traffic spikes
- Slow dependencies
- Cascading delays

---

## 9. Related Concepts

[[Latency]]
[[Tail Latency]]
[[Percentile Metrics]]

---

## 10. Interview Questions

- What contributes most to response time?
- How would you diagnose slow responses?

---

## 11. Summary

Response time is the total delay experienced by a user from request to response.