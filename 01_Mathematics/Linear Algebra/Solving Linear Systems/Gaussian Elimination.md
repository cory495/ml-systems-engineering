---
Created: 2026-06-27
Updated: 2026-06-27
tags:
  - linear-algebra
  - matrix-methods
  - systems-of-equations
Type: Notes
---

# Gaussian Elimination

Date: 2026-06-27

---

## 1. Problem

We need a systematic way to solve linear systems, compute matrix structure, and extract information like rank, null space, and invertibility.

Gaussian elimination reduces a matrix into a simpler equivalent form where solutions and structure become explicit.

Without it, solving linear systems is ad hoc and does not scale.

---

## 2. Intuition

Gaussian elimination is structured simplification.

You repeatedly eliminate variables to reduce a complex system into something triangular and easy to solve.

It transforms a matrix into a form where dependencies become visible.

---

## 3. How It Works

We use elementary row operations:

- swap rows
- scale rows
- add multiples of rows

Goal: transform \(A\) into row echelon form.

---

## 4. Key Components

- Pivot selection
- Row operations
- Forward elimination
- Back substitution

---

## 5. Tradeoffs

**Pros**
- systematic solution method
- reveals rank and structure
- computationally efficient

**Cons**
- numerical instability without pivoting
- O(n³) complexity

---

## 6. Scaling / Complexity

$$
O(n^3)
$$

---

## 7. Real Systems Usage

- solving Ax = b in engineering systems
- LU decomposition
- numerical solvers in ML and physics

---

## 8. Failure Modes

- division by small pivots
- floating point instability
- accumulated rounding error

---

## 9. Related Concepts

[[Row Echelon Form]]
[[Rank]]
[[Column Space]]
[[Null Space]]

---

## 10. Interview Questions

- Why does Gaussian elimination work?
- What is pivoting?
- Why is it O(n³)?

---

## 11. Summary

Gaussian elimination is a structured algorithm for solving linear systems and revealing matrix structure through systematic row reduction.