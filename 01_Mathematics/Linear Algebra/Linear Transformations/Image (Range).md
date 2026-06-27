---
Created: 2026-06-27
Updated: 2026-06-27
tags:
  - linear-algebra
  - subspaces
Type: Notes
---

# Image (Range)

Date: 2026-06-27

---

## 1. Problem

We need to know which outputs a linear transformation can produce.

The image describes all reachable outputs of a matrix.

---

## 2. Intuition

The image is the set of all outputs a transformation can reach.

It is the “output capability” of a matrix.

---

## 3. How It Works

$$
\text{Im}(A) = \{Ax \mid x \in \mathbb{R}^n\}
$$

$$
\text{Im}(A) = \text{Col}(A)
$$

---

## 4. Key Components

- Column space
- Rank
- Basis of image

---

## 5. Tradeoffs

**Pros**
- Captures system output space
- Directly tied to rank

**Cons**
- Not directly observable
- Hard in high dimensions

---

## 6. Scaling / Complexity

$$
O(n^3)
$$

---

## 7. Real Systems Usage

- PCA
- ML embeddings
- Regression
- Signal processing

---

## 8. Failure Modes

- Rank misestimation
- Numerical instability
- Noise inflating dimension

---

## 9. Related Concepts

[[Kernel]]
[[Rank]]
[[Linear Maps]]
[[Change of Basis]]

---

## 10. Interview Questions

- What is image of a matrix?
- How is it related to column space?

---

## 11. Summary

The image is the set of all outputs a linear transformation can produce and defines its reachability.