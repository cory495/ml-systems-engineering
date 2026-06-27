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
# Vertical Scaling

Date: 2026-06-15

---

## 1. Problem

How can we increase capacity without redesigning the system?

---

## 2. Intuition

Buy a bigger machine.

More CPU.
More memory.
Faster storage.

---

## 3. How It Works

- Upgrade hardware
- Increase resources
- Continue running the same software

---

## 4. Key Components

- CPU
- RAM
- SSDs
- Network interfaces

---

## 5. Tradeoffs

### Pros
- Simple
- Minimal software changes

### Cons
- Hardware limits exist
- Expensive
- Single point of failure

### When NOT to use it

For internet-scale systems.

---

## 6. Scaling / Complexity

Limited by physical hardware.

---

## 7. Real Systems Usage

- Traditional databases
- Enterprise servers
- Legacy systems

---

## 8. Failure Modes

- Hardware failure
- Resource exhaustion

---

## 9. Related Concepts

[[Horizontal Scaling]]
[[Scalability]]

---

## 10. Interview Questions

- When should vertical scaling be preferred?
- Why does horizontal scaling eventually dominate?

---

## 11. Summary

Vertical scaling increases capacity by upgrading a single machine. It is simple but has hard limits.