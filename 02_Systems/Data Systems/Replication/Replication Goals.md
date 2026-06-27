---
Created: 2026-06-27
Updated: 2026-06-27
tags:
  - systems
  - distributed-systems
  - replication
Type: Notes
---

# Replication Goals

Date: 2026-06-27

---

## 1. Problem

Distributed systems replicate data, but replication introduces tradeoffs between consistency, performance, and availability.

We need to clarify what replication is trying to optimize for.

---

## 2. Intuition

Replication is not just copying data—it is a design choice balancing competing goals.

Different systems prioritize different outcomes depending on workload and failure assumptions.

---

## 3. How It Works

Replication is typically optimized across:

1. Fault tolerance (survive node failures)
2. High availability (serve requests despite failures)
3. Read scalability (distribute read load)
4. Data durability (prevent data loss)
5. Geographic distribution (reduce latency globally)

---

## 4. Key Components

- replica topology
- consistency model
- failover mechanism
- routing layer
- synchronization protocol

---

## 5. Tradeoffs

### Pros
- improved reliability
- better performance scaling
- resilience to outages

### Cons
- increased system complexity
- consistency tradeoffs
- higher infrastructure cost
- harder debugging

---

## 6. Scaling / Complexity

More replicas improve:

$$
\text{availability} \uparrow
$$

but increase:

$$
\text{coordination cost} \uparrow
$$

---

## 7. Real Systems Usage

- globally distributed databases
- cloud storage systems
- streaming platforms
- CDN architectures

---

## 8. Failure Modes

- conflicting replication goals (e.g., strong consistency vs availability)
- misconfigured replication strategy
- unexpected latency spikes due to coordination overhead
- uneven replica distribution

Mitigations:
- clear SLA definitions
- consistency model selection (CP vs AP)
- workload-aware replication design

---

## 9. Related Concepts

[[Replication]]
[[Consistency]]
[[CAP Theorem]]
[[Leader-Based Replication]]
[[Fault Tolerance]]

---

## 10. Interview Questions

- What are the goals of replication?
- Why can’t we optimize all goals simultaneously?
- How do goals differ between OLTP and OLAP systems?
- How does geography affect replication design?

---

## 11. Summary

Replication exists to improve fault tolerance, availability, scalability, durability, and latency, but these goals conflict and force systems to make explicit tradeoffs in design.