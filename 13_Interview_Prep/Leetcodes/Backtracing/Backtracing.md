---
Type: Interview
Created: 2026-06-26
Updated: 2026-06-26
tags:
  - backtracking
  - recursion
  - dfs
  - interview-prep
  - backtracing
---

# Backtracking

## Core Idea
Backtracking is a controlled DFS approach where we build solutions incrementally and abandon (“backtrack”) paths that violate constraints.

---

## Key Properties
- Explore all possibilities via recursion
- Prune invalid states early
- Uses decision tree exploration
- Typically involves “choose → explore → unchoose”

---

## General Template

```python
def backtrack(state):
    if is_solution(state):
        result.append(state[:])
        return

    for choice in choices(state):
        if not valid(choice):
            continue

        make_choice(choice)
        backtrack(state)
        undo_choice(choice)
```

---

## Common Patterns

### 1. Subsets
Generate all subsets.

Examples:
- Subsets
- Subsets II

---

### 2. Permutations
Reorder elements.

Examples:
- Permutations
- Permutations II

---

### 3. Combination Search
Build combinations with constraints.

Examples:
- Combination Sum
- Combination Sum II
- Letter Combinations of a Phone Number

---

### 4. Grid Exploration
DFS on matrix with constraints.

Examples:
- Word Search
- N-Queens
- Sudoku Solver

---

## Complexity Cheat Sheet
- Time: O(branch^depth)
- Space: O(depth)
- Pruning is critical for performance

---

## Relevant Problems

### Easy
- down:: [[Subsets]]

### Medium
- down:: [[Permutations]]
- down:: [[Combination Sum]]
- down:: [[Combination Sum II]]
- down:: [[Word Search]]
- down:: [[Subsets II]]
- down::[[Generate Parentheses]]
- down:: [[Letter Combinations of a Phone Number]]
- down:: [[Palindrome Partitioning]]

### Hard