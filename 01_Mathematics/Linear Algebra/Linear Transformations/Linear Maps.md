---
Created: 2026-06-27
Updated: 2026-06-27
tags:
  - linear-algebra
  - transformations
  - mathematics
Type: Notes
---
# Linear Maps

Date: 2026-06-27

---

## 1. Problem

Linear maps define structure-preserving transformations between vector spaces. They are the backbone of nearly all computational linear algebra used in ML, signal processing, and systems.

Without linear maps, transformations become arbitrary functions with no composability, no algebraic guarantees, and no stable notion of dimensional structure.

---

## 2. Intuition

A linear map is a transformation that preserves addition and scaling.

It can rotate, scale, shear, or reflect space, but it cannot bend it.

A grid remains a grid—only its orientation and spacing change.

---

## 3. How It Works

A function \(T\) is linear if:

$$
T(x + y) = T(x) + T(y)
$$

$$
T(\alpha x) = \alpha T(x)
$$

Every linear map can be written as:

$$
T(x) = Ax
$$

---

## 4. Key Components

- Matrix representation \(A\)
- Basis vectors
- Linearity constraints
- Composition via matrix multiplication

---

## 5. Tradeoffs

**Pros**
- Efficient computation
- Composable
- Well-structured mathematically

**Cons**
- Cannot represent nonlinear relationships
- Limited expressiveness

---

## 6. Scaling / Complexity

$$
O(nm)
$$

---

## 7. Real Systems Usage

- Neural network layers
- PCA
- Signal processing
- Control systems

---

## 8. Failure Modes

- Rank deficiency
- Ill-conditioned matrices
- Loss of invertibility

---

## 9. Related Concepts

[[Affine Transformations]]
[[Kernel]]
[[Image (Range)]]
[[Change of Basis]]

---

## 10. Interview Questions

- Why can linear maps be written as matrices?
- What defines linearity?
- When is a linear map invertible?

---

## 11. Summary

Linear maps are structure-preserving transformations that form the foundation of computational linear algebra and ML systems.