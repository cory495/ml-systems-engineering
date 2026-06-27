---
Created: 2026-06-27
Updated: 2026-06-27
tags:
  - mathematics
  - linear-algebra
  - machine-learning
Type: Notes
---

# Linear Algebra

Date: 2026-06-27

---

## 1. Problem

Linear algebra exists to model and compute with systems of linear relationships at scale.

Most real-world data systems—machine learning models, signal processing pipelines, control systems, and distributed computations—reduce to operations on high-dimensional structured data. Without linear algebra, there is no scalable way to represent transformations, correlations, or geometry in these spaces.

It provides the mathematical backbone for:

- representing data as structured objects
- transforming data efficiently
- reasoning about high-dimensional geometry
- solving systems of equations that arise in modeling and optimization

---

## 2. Intuition

Linear algebra is the language of transformations.

Instead of thinking about numbers in isolation, it treats data as geometric objects:

- vectors = points or directions
- matrices = transformations of space
- systems of equations = constraints on geometry

A neural network layer, for example, is just a sequence of matrix multiplications that progressively reshape a vector space.

At its core, linear algebra is about answering:

> “What happens to space when we apply a transformation?”

---

## 3. How It Works

Linear algebra builds everything from two primitives:

### 1. Vectors
Objects representing magnitude and direction:

$$
x \in \mathbb{R}^n
$$

### 2. Linear transformations
Functions that preserve addition and scalar multiplication:

$$
T(ax + by) = aT(x) + bT(y)
$$

These are represented as matrices:

$$
T(x) = Ax
$$

where \(A\) is a matrix encoding the transformation.

From these primitives, we build:

- systems of equations
- projections
- rotations and scalings
- dimensionality reduction
- decompositions (SVD, eigenvalues)

---

## 4. Key Components

- Vectors: elements of vector spaces
- Matrices: linear transformations
- Basis: coordinate system for vector spaces
- Rank: dimensionality of transformation output
- Determinant: volume scaling factor
- Eigenvalues/eigenvectors: invariant directions under transformation
- Inner products: similarity measure between vectors

---

## 5. Tradeoffs

### Pros
- extremely expressive for modeling real systems
- computationally efficient and parallelizable
- forms foundation of ML and scientific computing
- well-understood geometric interpretation

### Cons
- limited to linear relationships unless extended
- high-dimensional intuition is non-trivial
- numerical instability in some operations (e.g., inversion)

### When NOT to use it
- highly nonlinear systems without linear approximation
- symbolic or discrete logic-heavy problems
- poorly conditioned numerical problems without regularization

---

## 6. Scaling / Complexity

Core operations:

- Matrix-vector multiplication:
  $$
  O(n^2)
  $$

- Matrix-matrix multiplication:
  $$
  O(n^3)
  $$

Optimized variants (Strassen, GPU kernels) reduce constants but not asymptotic structure.

Bottlenecks:
- memory bandwidth
- cache locality
- GPU parallelization limits
- numerical stability in large systems

---

## 7. Real Systems Usage

Linear algebra is foundational in:

- Machine Learning (neural networks, embeddings, PCA)
- Signal Processing (Fourier transforms, filtering)
- Computer Graphics (rotations, projections)
- Recommendation systems (matrix factorization)
- Robotics (state estimation, Kalman filters)
- Scientific computing (PDE solvers)

In ML systems specifically:
- model weights = matrices
- forward pass = matrix multiplication chain
- embeddings = vector spaces
- training = optimization in parameter space

---

## 8. Failure Modes

- Numerical instability (ill-conditioned matrices)
- Floating-point precision errors
- Rank deficiency causing non-invertibility
- Overfitting interpreted as geometric overparameterization
- Vanishing/exploding gradients in repeated matrix multiplication chains

Mitigations:
- regularization (L2, weight decay)
- normalization (batch/layer norm)
- SVD-based stabilization
- avoiding explicit matrix inversion when possible

---

## 9. Related Concepts

[[Vectors]]
[[Matrices]]
[[Matrix Multiplication]]
[[Eigenvalues and Eigenvectors]]
[[Singular Value Decomposition]]
[[Vector Spaces]]
[[Projection]]
[[Optimization]]
[[Probability Theory]]

---

## 10. Interview Questions

- What is a linear transformation?
- Why is matrix multiplication defined the way it is?
- What does rank represent geometrically?
- Why are eigenvectors important in ML?
- When is a matrix not invertible and why does it matter?
- How does linear algebra appear in neural networks?

---

## 11. Summary

Linear algebra is the mathematical framework for representing and transforming high-dimensional data. It models computation as geometric transformations of vector spaces using matrices. This makes it essential for machine learning, optimization, and systems that operate on structured data at scale. Its power comes from abstraction: complex real-world systems reduce to compositions of simple linear transformations.