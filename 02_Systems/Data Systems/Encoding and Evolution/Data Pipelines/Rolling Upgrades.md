---
Created: 2026-06-27
Updated: 2026-06-27
tags:
  - distributed-systems
  - deployment
  - systems
Type: Notes
---

# Rolling Upgrades

Date: 2026-06-27

---

## 1. Problem

In distributed systems, updating software is risky because the system must remain available while components are being replaced.

A naive upgrade approach (stopping all services and restarting them with a new version) causes downtime and can break clients.

Rolling upgrades solve this by gradually updating instances of a system without shutting it down.

---

## 2. Intuition

A rolling upgrade is like replacing parts of a running machine one component at a time while it continues operating.

Instead of upgrading everything at once, nodes are updated incrementally so that old and new versions coexist temporarily.

This requires strong compatibility guarantees between versions.

---

## 3. How It Works

1. System runs multiple instances of a service.
2. A subset of instances is taken out of load balancer rotation.
3. These instances are upgraded to a new version.
4. They are brought back online gradually.
5. The process repeats until all instances are upgraded.

Key requirement: new and old versions must be compatible during transition.

---

## 4. Key Components

### Load Balancer
Routes traffic away from nodes being upgraded.

### Service Instances
Individual nodes that run old or new versions.

### Deployment Controller
Orchestrates upgrade sequence.

### Health Checks
Ensure new instances are safe before receiving traffic.

---

## 5. Tradeoffs

### Pros

- Zero-downtime deployments
- Reduced risk of system-wide failure
- Incremental validation of new versions
- Scalable deployment strategy

### Cons

- Requires backward/forward compatibility
- Temporary version coexistence increases complexity
- Harder debugging across mixed versions
- Slower full deployment rollout

### When NOT to use it

For small systems or batch systems where downtime is acceptable, simpler full-restart deployments may be sufficient.

---

## 6. Scaling / Complexity

- Time: O(n) rollout across instances
- Space: duplicate running capacity during deployment (partial)

Bottlenecks:
- slow instance startup
- state migration complexity
- load balancer propagation delays

---

## 7. Real Systems Usage

- Kubernetes deployments (rolling update strategy)
- Microservice deployments in cloud environments
- Database cluster upgrades (replica-by-replica)
- Kafka broker upgrades
- Large-scale ML serving infrastructure upgrades

---

## 8. Failure Modes

- version skew between nodes causing inconsistent behavior
- incompatible schema changes breaking live traffic
- partial rollout leaving system in unstable state
- slow rollback in case of failure
- stateful services requiring migration complexity

---

## 9. Related Concepts

[[Backward Compatibility]]
[[Forward Compatibility]]
[[Schema Evolution]]
[[Dataflow Through Systems]]
[[Serialization]]

---

## 10. Interview Questions

- What is a rolling upgrade?
- Why is backward compatibility required for rolling deployments?
- What are risks of running mixed versions in production?
- How does Kubernetes implement rolling updates?
- How do you safely roll back a failed deployment?

---

## 11. Summary

Rolling upgrades are a deployment strategy where system components are updated incrementally without downtime. They rely heavily on backward and forward compatibility to ensure that old and new versions of a system can coexist safely during transition. This approach is essential for modern distributed systems that require high availability and continuous deployment.