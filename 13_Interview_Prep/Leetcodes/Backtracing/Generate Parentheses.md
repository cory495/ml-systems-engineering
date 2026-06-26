---
Difficulty: Medium
Topics: Backtracing
Created: 2026-06-01
Updated: 2026-06-26
tags:
  - interview
  - programming
  - backtracing
Type: Interview
---

# Generate Parentheses

This is a part of [[LeetCode Patterns]].

You are given an integer `n`. Return all well-formed parentheses strings that you can generate with `n` pairs of parentheses.

**Example 1:**

```java
Input: n = 1

Output: ["()"]
```

**Example 2:**

```java
Input: n = 3

Output: ["((()))","(()())","(())()","()(())","()()()"]
```

You may return the answer in **any order**.

**Constraints:**

- `1 <= n <= 7`

**Solutions:**

```python
class Solution:
    def generateParenthesis(self, n: int) -> List[str]:
        res = []

        def backtrack(to_add, open_ct, closed_ct):
            if len(to_add) == 2 * n:
                res.append(to_add)
                return
            if open_ct < n:
                backtrack(to_add + '(', open_ct + 1, closed_ct)
            if closed_ct < open_ct:
                backtrack(to_add + ')', open_ct, closed_ct + 1)
        backtrack("", 0, 0)
        return res
```
