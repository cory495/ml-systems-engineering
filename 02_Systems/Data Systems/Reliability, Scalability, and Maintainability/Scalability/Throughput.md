---
Created: 2026-06-01
Updated: 2026-06-26
tags:
  - systems
  - programming
  - databases
Type: Notes
---
# Throughput

Date: 2026-06-15

---

## 1. Problem

How much work can a system complete per unit time?

---

## 2. Intuition

Throughput measures system capacity.

A checkout line serving 100 customers per hour has higher throughput than one serving 50 customers per hour.

---

## 3. How It Works

- Requests arrive.
- Resources process requests.
- Completed work is measured over time.

Throughput = Work Completed / Time

---

## 4. Key Components

- Request rate
- Processing capacity
- Resource utilization
- Queue depth

---

## 5. Tradeoffs

### Pros
- Measures capacity
- Useful for planning growth

### Cons
- Doesn't reflect user experience
- Can hide latency issues

### When NOT to use it

When measuring perceived responsiveness.

---

## 6. Scaling / Complexity

### Bottlenecks

- CPU
- Disk
- Network
- Memory

---

## 7. Real Systems Usage

- Kafka messages/sec
- PostgreSQL transactions/sec
- Spark records/sec
- LLM tokens/sec

---

## 8. Failure Modes

- Queue buildup
- Resource saturation
- Cascading failures

---

## 9. Related Concepts

[[Latency]]
[[Tail Latency]]
[[Load Parameters]]

---

## 10. Interview Questions

- Difference between throughput and latency?
- Can throughput improve while latency worsens?

---

## 11. Summary

Throughput measures how much work a system performs over time. High throughput indicates capacity but does not guarantee good responsiveness.