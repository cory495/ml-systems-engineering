---
Created: 2026-06-27
Updated: 2026-06-27
tags:
  - linear-algebra
Type: Notes
---

# Orthogonal Matrix

Date: 2026-06-27

---

## 1. Problem

We need transformations that preserve lengths and angles.

---

## 2. Intuition

Orthogonal matrices represent rotations and reflections.

They preserve geometry exactly.

---

## 3. How It Works

$$
Q^T Q = I
$$

So:

$$
Q^{-1} = Q^T
$$

---

## 4. Key Components

- orthonormal columns
- rotation/reflection structure
- inverse equals transpose

---

## 5. Tradeoffs

**Pros**
- numerically stable
- preserves geometry
- efficient inversion

**Cons**
- restricted class of transformations

---

## 6. Scaling / Complexity

$$
O(n^2)
$$

for applying to vectors.

---

## 7. Real Systems Usage

- QR decomposition
- PCA rotations
- computer graphics
- signal processing

---

## 8. Failure Modes

- loss of orthogonality due to numerical drift
- misuse in non-orthogonal contexts

---

## 9. Related Concepts

[[Matrix Transpose]]
[[Symmetric Matrix]]
[[Matrix Inverse]]

---

## 10. Interview Questions

- Why is inverse equal to transpose?
- What does orthogonal mean geometrically?

---

## 11. Summary

Orthogonal matrices preserve lengths and angles and represent rotations and reflections in vector spaces.