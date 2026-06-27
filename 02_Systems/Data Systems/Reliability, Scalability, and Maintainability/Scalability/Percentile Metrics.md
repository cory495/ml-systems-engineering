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
# Percentile Metrics

Date: 2026-06-15

---

## 1. Problem

Why are averages misleading?

---

## 2. Intuition

If 99 requests take 10 ms and 1 request takes 1000 ms:

Average ≈ 20 ms

The average looks good, but one user had a terrible experience.

Percentiles reveal these outliers.

---

## 3. How It Works

P50 = 50% of requests are faster

P95 = 95% of requests are faster

P99 = 99% of requests are faster

---

## 4. Key Components

- P50
- P90
- P95
- P99
- P999

---

## 5. Tradeoffs

### Pros
- Reveals performance outliers
- Better reflects user experience

### Cons
- More difficult to interpret
- Requires large datasets

### When NOT to use it

For tiny sample sizes.

---

## 6. Scaling / Complexity

Storage and computation increase with monitoring detail.

---

## 7. Real Systems Usage

- Google Search
- AWS
- Cloud monitoring dashboards
- LLM serving systems

---

## 8. Failure Modes

- Hidden tail latency
- Poor monitoring
- Incomplete metrics

---

## 9. Related Concepts

[[Tail Latency]]
[[Latency]]
[[Response Time]]

---

## 10. Interview Questions

- Why is P99 more useful than averages?
- Why does Google focus on percentiles?

---

## 11. Summary

Percentiles measure the distribution of latency and reveal slow outliers that averages hide.