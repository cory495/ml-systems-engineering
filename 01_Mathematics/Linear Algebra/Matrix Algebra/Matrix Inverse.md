---
Created: 2026-06-27
Updated: 2026-06-27
tags:
  - linear-algebra
Type: Notes
---

# Matrix Inverse

Date: 2026-06-27

---

## 1. Problem

We need a way to reverse linear transformations when possible.

---

## 2. Intuition

The inverse undoes a transformation.

If a matrix stretches space, its inverse unstretches it.

---

## 3. How It Works

$$
A A^{-1} = I
$$

Exists only if matrix is full rank.

---

## 4. Key Components

- invertibility
- determinant non-zero condition
- full rank requirement

---

## 5. Tradeoffs

**Pros**
- reversibility
- solves linear systems

**Cons**
- expensive to compute
- unstable for ill-conditioned matrices

---

## 6. Scaling / Complexity

$$
O(n^3)
$$

---

## 7. Real Systems Usage

- solving Ax = b
- optimization
- control systems

---

## 8. Failure Modes

- numerical instability
- singular matrices
- amplification of noise

---

## 9. Related Concepts

[[Matrix Multiplication]]
[[Identity Matrix]]
[[Orthogonal Matrix]]

---

## 10. Interview Questions

- When does an inverse exist?
- Why is inversion unstable?

---

## 11. Summary

Matrix inverse reverses linear transformations when the matrix is full rank and well-conditioned.