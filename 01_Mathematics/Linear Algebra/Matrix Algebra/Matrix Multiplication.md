---
Created: 2026-06-27
Updated: 2026-06-27
tags:
  - linear-algebra
  - computation
Type: Notes
---

# Matrix Multiplication

Date: 2026-06-27

---

## 1. Problem

We need a way to compose linear transformations efficiently.

Matrix multiplication represents function composition of linear maps.

---

## 2. Intuition

Matrix multiplication is applying one transformation after another.

If one matrix rotates space and another scales it, multiplication combines both effects.

Order matters because transformations are directional.

---

## 3. How It Works

Given matrices \(A\) and \(B\):

$$
(AB)x = A(Bx)
$$

Entry-wise:

$$
(AB)_{ij} = \sum_k A_{ik} B_{kj}
$$

---

## 4. Key Components

- row-by-column dot products
- associativity
- non-commutativity
- composition of linear maps

---

## 5. Tradeoffs

**Pros**
- enables composition
- preserves linear structure
- widely optimized in hardware

**Cons**
- expensive for large matrices
- non-commutative
- can amplify numerical errors

---

## 6. Scaling / Complexity

$$
O(n^3)
$$

(classical multiplication)

---

## 7. Real Systems Usage

- neural network forward passes
- graphics pipelines
- scientific simulations
- graph algorithms

---

## 8. Failure Modes

- numerical instability
- overflow/underflow
- poor cache performance

---

## 9. Related Concepts

[[Matrices]]
[[Identity Matrix]]
[[Matrix Inverse]]
[[Block Matrices]]

---

## 10. Interview Questions

- Why is matrix multiplication defined this way?
- Why is it not commutative?
- What does it represent geometrically?

---

## 11. Summary

Matrix multiplication represents composition of linear transformations and is fundamental to computation in linear algebra and machine learning.