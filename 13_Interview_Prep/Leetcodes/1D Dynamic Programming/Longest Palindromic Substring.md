---
Created: 2026-06-01
Updated: 2026-06-26
tags:
  - interview
  - programming
Type: Interview
Difficulty: Medium
Topics: 1D Dynamic Programming
---
# Longest Palindromic Substring

This is a part of [[LeetCode Patterns]].

Given a string `s`, return the longest substring of `s` that is a _palindrome_.

A **palindrome** is a string that reads the same forward and backward.

If there are multiple palindromic substrings that have the same length, return any one of them.

**Example 1:**

```java
Input: s = "ababd"

Output: "bab"
```

Explanation: Both "aba" and "bab" are valid answers.

**Example 2:**

```java
Input: s = "abbc"

Output: "bb"
```

**Constraints:**

- `1 <= s.length <= 1000`
- `s` contains only digits and English letters.

**Solutions:**

```python
class Solution:
    def longestPalindrome(self, s: str) -> str:
        l = r = 0
        max_str = ""
        n = len(s)

        while r < n:
            while s[l:r+1] != s[l:r+1][::-1]:
                l += 1
            if r-l+1 > len(max_str):
                max_str = s[l:r+1]
            r += 1
            l = 0
        return max_str
```
