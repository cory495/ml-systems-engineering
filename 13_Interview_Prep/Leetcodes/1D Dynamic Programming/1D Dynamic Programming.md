---
Type: Interview
Created: 2026-06-26
Updated: 2026-06-26
tags:
  - algorithms
  - interview-prep
  - dynamic-programming
---

# 1D Dynamic Programming

## Core Idea
1D Dynamic Programming is used when a problem can be broken into overlapping subproblems along a single dimension (usually index or value), where the optimal solution at each step depends on previous results.

---

## Key Properties
- Optimal substructure: solution builds from smaller subproblems.
- Overlapping subproblems: same states are reused.
- Typically uses an array `dp[i]` where each index represents a state.
- Transitions depend only on earlier indices.

---

## General DP Template

```python
dp = [0] * (n + 1)

for i in range(1, n + 1):
    dp[i] = transition(dp[i-1], dp[i-2], ...)
```

---

## Common Patterns

### 1. Linear Recurrence
Each state depends on previous states.

Examples:
- Fibonacci Number
- Climbing Stairs
- House Robber

---

### 2. Take or Skip
At each index, choose whether to include current element.

Examples:
- House Robber
- Maximum Subarray
- Delete and Earn

---

### 3. Prefix-Based DP
Build solution using prefix accumulation.

Examples:
- Climbing Stairs
- Minimum Cost Climbing Stairs
- Decode Ways

---

### 4. Subsequence DP
Track best solution up to index.

Examples:
- Longest Increasing Subsequence (1D optimized version)
- Maximum Product Subarray
- Partition Equal Subset Sum (1D knapsack)

---

### 5. Knapsack (1D Optimization)
Compress 2D DP into 1D.

Examples:
- 0/1 Knapsack
- Coin Change
- Combination Sum IV

---

## Common Interview Problems
- Climbing Stairs
- House Robber
- House Robber II
- Coin Change
- Combination Sum IV
- Decode Ways
- Maximum Subarray
- Partition Equal Subset Sum
- Jump Game
- Word Break

---

## Complexity Cheat Sheet
- Time: O(n) to O(n × k) depending on transitions
- Space: O(n) → often optimizable to O(1)
- Key optimization: reuse previous DP states

---

## Relevant Problems

### Easy
- [[Climbing Stairs]]
- [[Min Climbing Stairs]]
### Medium
- [[House Robbers]]
- [[House Robber II]]
- [[Longest Increasing Subsequence]]
- [[Longest Palindromic Substring]]
- [[Palindromic Substrings]]
### Hard