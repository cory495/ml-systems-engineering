---
Created: 2026-06-27
Updated: 2026-06-27
tags:
  - linear-algebra
  - matrix-properties
Type: Notes
---

# Rank

Date: 2026-06-27

---

## 1. Problem

We need a single measure of how much independent information a matrix contains.

Rank quantifies the dimensionality of the space spanned by a matrix.

---

## 2. Intuition

Rank is the number of independent directions in a matrix.

It tells you how much of the output space is actually reachable.

---

## 3. How It Works

Rank is defined as:

$$
\text{rank}(A) = \dim(\text{Col}(A))
$$

Equivalently:

$$
\text{rank}(A) = \dim(\text{Row}(A))
$$

---

## 4. Key Components

- pivot count
- column space dimension
- row space dimension
- linear independence

---

## 5. Tradeoffs

**Pros**
- measures information content
- determines invertibility
- central to linear algebra structure

**Cons**
- sensitive to numerical precision
- hard to compute exactly in noisy data

---

## 6. Scaling / Complexity

$$
O(n^3)
$$

via elimination or decomposition.

---

## 7. Real Systems Usage

- PCA dimensionality
- regression stability
- neural network expressivity
- signal processing

---

## 8. Failure Modes

- near-dependent vectors causing instability
- floating point misclassification
- noise inflating rank estimate

---

## 9. Related Concepts

[[Column Space]]
[[Row Space]]
[[Null Space]]
[[Gaussian Elimination]]

---

## 10. Interview Questions

- What does rank represent?
- How is rank computed?
- Why is rank important for invertibility?

---

## 11. Summary

Rank measures the number of independent directions in a matrix and determines its effective dimensionality and information content.