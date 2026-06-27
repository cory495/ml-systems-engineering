---
Created: 2026-06-27
Updated: 2026-06-27
tags:
  - linear-algebra
  - transformations
Type: Notes
---

# Change of Basis

Date: 2026-06-27

---

## 1. Problem

The same vector or transformation can look different depending on the coordinate system.

We need a way to convert representations between bases.

---

## 2. Intuition

Change of basis is a change in coordinate language, not geometry.

The object stays the same; only its representation changes.

---

## 3. How It Works

Coordinate transform:

$$
[x]_C = P_{B \to C}[x]_B
$$

Matrix transform:

$$
A_C = P^{-1} A_B P
$$

---

## 4. Key Components

- Basis vectors
- Change of basis matrix
- Similarity transform

---

## 5. Tradeoffs

**Pros**
- Simplifies computation
- Reveals structure

**Cons**
- Requires matrix inversion
- Can be numerically unstable

---

## 6. Scaling / Complexity

$$
O(n^3)
$$

---

## 7. Real Systems Usage

- PCA
- Graphics pipelines
- Robotics frames
- Quantum mechanics

---

## 8. Failure Modes

- Incorrect inversion
- Floating point drift
- Basis inconsistency

---

## 9. Related Concepts

[[Linear Maps]]
[[Affine Transformations]]
[[Image (Range)]]
[[Kernel]]

---

## 10. Interview Questions

- What is a basis?
- Why is similarity transformation used?

---

## 11. Summary

Change of basis converts vector and operator representations between coordinate systems while preserving geometry.