---
Created: 2026-06-01
Updated: 2026-06-26
tags:
  - interview
  - programming
  - backtracing
Type: Interview
Difficulty: Medium
Topics: Backtracing
---
# Palindrome Partitioning

This is a part of [[LeetCode Patterns]].

Given a string `s`, split `s` into substrings where every substring is a palindrome. Return all possible lists of palindromic substrings.

You may return the solution in **any order**.

**Example 1:**

```java
Input: s = "aab"

Output: [["a","a","b"],["aa","b"]]
```

**Example 2:**

```java
Input: s = "a"

Output: [["a"]]
```

**Constraints:**

- `1 <= s.length <= 20`
- `s` contains only lowercase English letters.

**Solutions:**

```python
class Solution:
    def partition(self, s: str) -> List[List[str]]:
        res = []
        n = len(s)
        def backtrack(left, to_add):
            if left == n:
                res.append(to_add[:])
                return
            for i in range(left+1, n+1):
                if s[left:i] == s[left:i][::-1]:
                    to_add.append(s[left:i])
                    backtrack(i, to_add)
                    to_add.pop()
        
        backtrack(0, [])
        return res
```
