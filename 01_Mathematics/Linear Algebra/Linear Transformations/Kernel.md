---
Created: 2026-06-27
Updated: 2026-06-27
tags:
  - linear-algebra
  - subspaces
Type: Notes
---

# Kernel

Date: 2026-06-27

---

## 1. Problem

We need to understand which inputs a transformation collapses to zero.

This captures information loss and redundancy.

---

## 2. Intuition

The kernel is everything a matrix cannot “see.”

These are inputs that vanish after transformation.

---

## 3. How It Works

$$
\text{Ker}(A) = \{x \mid Ax = 0\}
$$

---

## 4. Key Components

- Null space
- Nullity
- Basis of kernel

---

## 5. Tradeoffs

**Pros**
- Reveals redundancy
- Determines invertibility

**Cons**
- Can be high-dimensional
- Numerically unstable

---

## 6. Scaling / Complexity

$$
O(n^3)
$$

---

## 7. Real Systems Usage

- Regression degeneracy
- PCA
- ML redundancy
- Control systems

---

## 8. Failure Modes

- Floating point misclassification
- Ill-conditioned matrices

---

## 9. Related Concepts

[[Image (Range)]]
[[Rank]]
[[Linear Maps]]
[[Change of Basis]]

---

## 10. Interview Questions

- What is kernel?
- Why does Ax = 0 matter?

---

## 11. Summary

The kernel is the set of all inputs mapped to zero, capturing information loss in linear transformations.