# Horizontal Scaling

Date: 2026-06-15

---

## 1. Problem

How can we increase capacity beyond a single machine?

---

## 2. Intuition

Instead of buying a bigger server, add more servers.

Scale out rather than scale up.

---

## 3. How It Works

- Add machines
- Distribute workload
- Balance traffic
- Replicate data

---

## 4. Key Components

- Load balancing
- Sharding
- Replication
- Distributed systems

---

## 5. Tradeoffs

### Pros
- Virtually unlimited growth
- Improved fault tolerance

### Cons
- Increased complexity
- Distributed systems challenges

### When NOT to use it

For small workloads.

---

## 6. Scaling / Complexity

Adds networking and coordination overhead.

---

## 7. Real Systems Usage

- Google
- Amazon
- Kafka
- Cassandra

---

## 8. Failure Modes

- Network partitions
- Uneven load distribution
- Coordination failures

---

## 9. Related Concepts

[[Vertical Scaling]]
[[Scalability]]
[[Load Balancing]]
[[Replication]]

---

## 10. Interview Questions

- Why is horizontal scaling harder?
- What challenges arise when adding machines?

---

## 11. Summary

Horizontal scaling increases capacity by adding more machines and distributing work across them.