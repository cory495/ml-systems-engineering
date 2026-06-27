---
Created: 2026-06-27
Updated: 2026-06-27
tags:
  - systems
  - distributed-systems
  - fault-tolerance
Type: Notes
---

# Failover

Date: 2026-06-27

---

## 1. Problem

Nodes in distributed systems can fail due to hardware issues, network partitions, or software crashes.

We need a mechanism to continue serving requests despite node failures.

---

## 2. Intuition

Failover is “automatic switching to a backup.”

When a node fails, another node takes over its responsibilities.

---

## 3. How It Works

1. Health checks detect node failure
2. Coordinator marks node as unavailable
3. Traffic is redirected to replica or standby node
4. State is restored via replication or replay logs
5. System continues serving requests

Types:
- active-passive failover
- active-active failover

---

## 4. Key Components

- health monitoring system
- load balancer / routing layer
- replica nodes
- state synchronization mechanism

---

## 5. Tradeoffs

### Pros
- high availability
- resilience to node failure
- minimal downtime

### Cons
- complexity in state synchronization
- potential brief inconsistencies
- failover latency

---

## 6. Scaling / Complexity

Detection:

$$
O(1) \text{ per heartbeat interval}
$$

Failover propagation:

$$
O(n)
$$

---

## 7. Real Systems Usage

- cloud load balancers
- database replication systems
- Kubernetes pod rescheduling
- distributed storage systems

---

## 8. Failure Modes

- false positives causing unnecessary failover
- split-brain during failover
- stale state replication
- failover storms in large clusters

Mitigations:
- quorum-based health checks
- leader election protocols
- gradual traffic shifting
- fencing tokens

---

## 9. Related Concepts

[[Quorums]]
[[Network Partitions]]
[[Split Brain]]
[[Anti-Entropy]]
[[Metadata Service]]

---

## 10. Interview Questions

- What is failover?
- What is active-active vs active-passive?
- How do systems avoid split-brain during failover?
- What triggers failover?

---

## 11. Summary

Failover is a fault tolerance mechanism that redirects traffic from failed nodes to healthy replicas, ensuring continued service availability despite node or network failures.