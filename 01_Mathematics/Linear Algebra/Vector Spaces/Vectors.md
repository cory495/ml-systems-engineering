---
Created: 2026-06-27
Updated: 2026-06-27
tags:
  - linear-algebra
  - vector-spaces
Type: Concept
---

# Vectors

Date: 2026-06-27

---

## 1. Problem

We need a way to represent quantities that have both magnitude and direction in structured spaces.

Vectors generalize scalars into multi-dimensional representations used in geometry, ML, and physics.

---

## 2. Intuition

A vector is an arrow in space.

It represents direction and magnitude, but more generally it is an element of a vector space—not necessarily geometric.

In ML, vectors are feature representations.

---

## 3. How It Works

A vector in \( \mathbb{R}^n \):

$$
x = (x_1, x_2, \dots, x_n)
$$

Operations:

$$
x + y, \quad \alpha x
$$

---

## 4. Key Components

- components
- direction
- magnitude (norm)
- basis representation

---

## 5. Tradeoffs

**Pros**
- expressive representation
- supports linear structure
- easy to compute with

**Cons**
- depends on basis
- interpretation can be non-physical in high dimensions

---

## 6. Scaling / Complexity

$$
O(n)
$$

---

## 7. Real Systems Usage

- embeddings in ML
- physical motion
- signal representations
- state vectors in control systems

---

## 8. Failure Modes

- scale sensitivity
- high-dimensional sparsity issues
- poor normalization

---

## 9. Related Concepts

[[Scalars]]
[[Vector Spaces]]
[[Span]]
[[Basis]]

---

## 10. Interview Questions

- What is a vector?
- How does it differ from a scalar?

---

## 11. Summary

Vectors are elements of vector spaces representing structured quantities with direction and magnitude, foundational to geometry, ML, and physics.