---
Created: 2026-06-27
Updated: 2026-06-27
tags:
  - linear-algebra
  - vector-spaces
Type: Concept
---

# Dimension

Date: 2026-06-27

---

## 1. Problem

We need a way to measure the complexity or degrees of freedom of a vector space.

Dimension captures the number of independent directions in a space.

---

## 2. Intuition

Dimension is how many independent axes you need to describe every vector.

It is the size of a basis.

---

## 3. How It Works

$$
\dim(V) = \text{number of vectors in a basis of } V
$$

---

## 4. Key Components

- basis size
- degrees of freedom
- independence

---

## 5. Tradeoffs

**Pros**
- compact descriptor of space
- fundamental invariant

**Cons**
- depends on abstract basis existence

---

## 6. Scaling / Complexity

$$
O(1)
$$

once basis is known

---

## 7. Real Systems Usage

- embedding dimensionality
- PCA reduction
- model complexity
- signal subspaces

---

## 8. Failure Modes

- misestimating intrinsic dimension
- noise inflating dimensionality

---

## 9. Related Concepts

[[Basis]]
[[Span]]
[[Linear Independence]]
[[Vector Spaces]]

---

## 10. Interview Questions

- What is dimension?
- Why is it invariant?

---

## 11. Summary

Dimension measures the number of independent directions in a vector space and equals the size of any basis.