---
Created: 2026-06-27
Updated: 2026-06-27
tags:
  - linear-algebra
  - vector-spaces
Type: Concept
---

# Subspaces

Date: 2026-06-27

---

## 1. Problem

We often need smaller structured sets within vector spaces that preserve linear properties.

Subspaces capture closed linear structure inside a larger vector space.

---

## 2. Intuition

A subspace is a “mini vector space inside a vector space.”

If you stay inside it, linear combinations never take you outside.

---

## 3. How It Works

A subset \(W \subseteq V\) is a subspace if:

$$
x + y \in W, \quad \alpha x \in W
$$

and contains zero vector:

$$
0 \in W
$$

---

## 4. Key Components

- closure under addition
- closure under scalar multiplication
- zero vector inclusion

---

## 5. Tradeoffs

**Pros**
- simplifies analysis
- captures structure of solutions
- reduces dimensionality reasoning

**Cons**
- may be hard to identify in high dimensions

---

## 6. Scaling / Complexity

Depends on basis computation:

$$
O(n^3)
$$

---

## 7. Real Systems Usage

- null spaces
- column spaces
- PCA subspaces
- constraint manifolds

---

## 8. Failure Modes

- confusing subset vs subspace
- ignoring zero vector requirement

---

## 9. Related Concepts

[[Vector Spaces]]
[[Span]]
[[Basis]]
[[Null Space]]

---

## 10. Interview Questions

- What makes a subset a subspace?
- Why must zero vector be included?

---

## 11. Summary

Subspaces are subsets of vector spaces that preserve linear structure under addition and scalar multiplication.