---
Created: 2026-06-27
Updated: 2026-06-27
tags:
  - linear-algebra
  - subspaces
Type: Notes
---

# Null Space

Date: 2026-06-27

---

## 1. Problem

We need to identify all inputs that a matrix maps to zero.

This captures redundancy, degeneracy, and loss of information in linear systems.

---

## 2. Intuition

Null space is the set of invisible directions of a transformation.

These inputs disappear completely after transformation.

---

## 3. How It Works

$$
\text{Null}(A) = \{x \mid Ax = 0\}
$$

Solve using:

$$
Ax = 0
$$

via row reduction.

---

## 4. Key Components

- homogeneous system
- basis of null space
- nullity
- free variables

---

## 5. Tradeoffs

**Pros**
- reveals redundancy
- essential for invertibility
- defines solution structure

**Cons**
- can be high-dimensional
- numerically unstable

---

## 6. Scaling / Complexity

$$
O(n^3)
$$

---

## 7. Real Systems Usage

- regression degeneracy
- PCA interpretation
- ML redundancy
- control systems

---

## 8. Failure Modes

- floating point misclassification
- near-singular systems
- ill-conditioning

---

## 9. Related Concepts

[[Rank]]
[[Column Space]]
[[Row Space]]
[[Gaussian Elimination]]

---

## 10. Interview Questions

- What is null space?
- How does it relate to rank?
- Why does Ax = 0 matter?

---

## 11. Summary

Null space is the set of all vectors mapped to zero by a matrix, capturing redundancy and loss of information in linear transformations.