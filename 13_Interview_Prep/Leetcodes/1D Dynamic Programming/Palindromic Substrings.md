---
Created: 2026-06-01
Updated: 2026-06-26
tags:
  - interview
  - programming
  - dynamic-programming
Type: Interview
Difficulty: Medium
Topics: 1D Dynamic Programming
---
# Palindromic Substrings

This is a part of [[LeetCode Patterns]].

Given a string `s`, return the number of substrings within `s` that are palindromes.

A **palindrome** is a string that reads the same forward and backward.

**Example 1:**

```java
Input: s = "abc"

Output: 3
```

Explanation: "a", "b", "c".

**Example 2:**

```java
Input: s = "aaa"

Output: 6
```

Explanation: "a", "a", "a", "aa", "aa", "aaa". Note that different substrings are counted as different palindromes even if the string contents are the same.

**Constraints:**

- `1 <= s.length <= 1000`
- `s` consists of lowercase English letters.

**Solutions:**

```python
class Solution:
    def countSubstrings(self, s: str) -> int:
        l = r = 0
        ct = 0
        n = len(s)

        while r < n:
            while l <= r:
                if s[l:r+1] == s[l:r+1][::-1]:
                    ct += 1
                l += 1
            r += 1
            l = 0
        return ct
```
