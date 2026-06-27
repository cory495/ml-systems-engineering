---
Created: 2026-06-27
Updated: 2026-06-27
tags:
  - linear-algebra
  - vector-spaces
Type: Concept
---

# Basis

Date: 2026-06-27

---

## 1. Problem

We need a minimal set of vectors that can represent an entire vector space without redundancy.

Basis provides the coordinate system for vector spaces.

---

## 2. Intuition

A basis is the smallest set of directions needed to describe a space.

Every vector in the space can be uniquely expressed using basis vectors.

---

## 3. How It Works

A set \( \{v_1, \dots, v_n\} \) is a basis if:

- it spans the space
- it is linearly independent

---

## 4. Key Components

- spanning set
- linear independence
- coordinate representation
- uniqueness of representation

---

## 5. Tradeoffs

**Pros**
- minimal representation
- unique coordinates
- simplifies computation

**Cons**
- basis choice affects interpretation
- changing basis is costly

---

## 6. Scaling / Complexity

$$
O(n^3)
$$

---

## 7. Real Systems Usage

- PCA eigenbasis
- coordinate systems in robotics
- embeddings
- feature transformations

---

## 8. Failure Modes

- poor basis choice leading to instability
- numerical conditioning issues

---

## 9. Related Concepts

[[Span]]
[[Linear Independence]]
[[Dimension]]
[[Vector Spaces]]

---

## 10. Interview Questions

- What is a basis?
- Why is representation unique?

---

## 11. Summary

A basis is a minimal set of vectors that spans a vector space and allows unique representation of all vectors.