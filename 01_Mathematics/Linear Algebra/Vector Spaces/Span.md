---
Created: 2026-06-27
Updated: 2026-06-27
tags:
  - linear-algebra
  - vector-spaces
Type: Concept
---

# Span

Date: 2026-06-27

---

## 1. Problem

We need a way to describe all possible vectors that can be generated from a given set of vectors.

Span defines the reach of linear combinations.

---

## 2. Intuition

Span is everything you can build from a set of vectors using addition and scaling.

It defines the expressive power of a set of directions.

---

## 3. How It Works

For vectors \(v_1, \dots, v_k\):

$$
\text{span}(v_1, \dots, v_k) =
\left\{
\sum_{i=1}^k \alpha_i v_i
\right\}
$$

---

## 4. Key Components

- linear combinations
- generating set
- basis relationship

---

## 5. Tradeoffs

**Pros**
- defines reachable space
- foundational for basis and dimension

**Cons**
- redundant representations possible
- computationally expensive in large sets

---

## 6. Scaling / Complexity

$$
O(nk)
$$

---

## 7. Real Systems Usage

- feature spaces in ML
- PCA subspaces
- signal reconstruction
- embeddings

---

## 8. Failure Modes

- linear dependence inflating representation
- redundant vectors

---

## 9. Related Concepts

[[Linear Independence]]
[[Basis]]
[[Vector Spaces]]
[[Subspaces]]

---

## 10. Interview Questions

- What is span?
- How does span relate to basis?

---

## 11. Summary

Span is the set of all linear combinations of a set of vectors, defining the space they generate.