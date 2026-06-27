---
Created: 2026-06-27
Updated: 2026-06-27
tags:
  - linear-algebra
  - subspaces
Type: Notes
---

# Column Space

Date: 2026-06-27

---

## 1. Problem

We need to understand which outputs a matrix can produce from linear combinations of its columns.

Column space defines the reachable output subspace of a linear transformation.

---

## 2. Intuition

Column space is all combinations of the columns of a matrix.

It is the space of all possible outputs Ax can produce.

---

## 3. How It Works

$$
\text{Col}(A) = \{Ax \mid x \in \mathbb{R}^n\}
$$

Equivalently:

$$
\text{Col}(A) = \text{span}(\text{columns of } A)
$$

---

## 4. Key Components

- spanning set (columns)
- linear independence
- basis of column space
- dimension = rank

---

## 5. Tradeoffs

**Pros**
- captures output behavior
- directly tied to rank
- useful for solving systems

**Cons**
- hard to visualize in high dimensions
- requires decomposition to compute

---

## 6. Scaling / Complexity

$$
O(n^3)
$$

---

## 7. Real Systems Usage

- PCA
- embeddings
- regression models
- feature spaces in ML

---

## 8. Failure Modes

- dependent columns reducing expressivity
- numerical instability
- misestimated rank

---

## 9. Related Concepts

[[Rank]]
[[Row Space]]
[[Null Space]]
[[Image (Range)]]

---

## 10. Interview Questions

- What is column space?
- How is it related to rank?
- Why does Ax depend only on column space?

---

## 11. Summary

Column space is the span of the columns of a matrix and represents all possible outputs of a linear transformation.