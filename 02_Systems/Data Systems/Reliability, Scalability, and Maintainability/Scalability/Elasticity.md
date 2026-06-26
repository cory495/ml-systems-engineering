---
Created: 2026-06-01
Updated: 2026-06-26
tags:
  - systems
  - programming
  - databases
Type: Notes
---
# Elasticity

Date: 2026-06-15

---

## 1. Problem

How can a system automatically adapt to changing load?

---

## 2. Intuition

Scalability means a system can grow.

Elasticity means it can grow and shrink automatically.

---

## 3. How It Works

- Monitor load
- Detect thresholds
- Add resources
- Remove resources when demand drops

---

## 4. Key Components

- Autoscaling
- Monitoring
- Resource provisioning
- Cloud infrastructure

---

## 5. Tradeoffs

### Pros
- Cost efficiency
- Handles traffic spikes

### Cons
- Increased operational complexity
- Scaling delays

### When NOT to use it

For static workloads.

---

## 6. Scaling / Complexity

Requires monitoring and orchestration systems.

---

## 7. Real Systems Usage

- AWS Auto Scaling
- Kubernetes
- Cloud-native applications

---

## 8. Failure Modes

- Incorrect scaling thresholds
- Oscillating scale events
- Slow provisioning

---

## 9. Related Concepts

[[Scalability]]
[[Horizontal Scaling]]
[[Load Parameters]]

---

## 10. Interview Questions

- Difference between scalability and elasticity?
- What causes autoscaling failures?

---

## 11. Summary

Elasticity allows systems to automatically add or remove resources as load changes, improving efficiency and responsiveness.