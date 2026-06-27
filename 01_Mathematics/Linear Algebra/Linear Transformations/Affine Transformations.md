---
Created: 2026-06-27
Updated: 2026-06-27
tags:
  - linear-algebra
  - transformations
Type: Notes
---

# Affine Transformations

Date: 2026-06-27

---

## 1. Problem

Linear maps cannot represent translations because they always fix the origin. Many real systems require both linear transformation and translation.

Affine transformations extend linear maps to include shifts.

---

## 2. Intuition

Affine transformations are linear maps plus a shift.

They move objects in space without bending them.

---

## 3. How It Works

Affine form:

$$
T(x) = Ax + b
$$

Homogeneous representation:

$$
\begin{bmatrix}
A & b \\
0 & 1
\end{bmatrix}
$$

---

## 4. Key Components

- Linear part \(A\)
- Translation \(b\)
- Homogeneous coordinates

---

## 5. Tradeoffs

**Pros**
- More expressive than linear maps
- Preserves lines and parallelism

**Cons**
- More complex representation
- Requires homogeneous coordinates

---

## 6. Scaling / Complexity

$$
O(n^2)
$$

---

## 7. Real Systems Usage

- Computer graphics
- Robotics
- Camera transforms
- ML augmentation

---

## 8. Failure Modes

- Incorrect composition order
- Floating point drift
- Homogeneous coordinate mistakes

---

## 9. Related Concepts

[[Linear Maps]]
[[Change of Basis]]
[[Image (Range)]]
[[Kernel]]

---

## 10. Interview Questions

- Difference between linear and affine maps?
- Why homogeneous coordinates?

---

## 11. Summary

Affine transformations extend linear maps with translation, enabling full geometric transformations used in graphics, robotics, and ML.