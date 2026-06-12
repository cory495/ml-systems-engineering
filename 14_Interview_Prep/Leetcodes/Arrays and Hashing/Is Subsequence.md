---
Difficulty: Easy
Topics: Arrays
---

# Is Subsequence

This is a part of [[LeetCode Patterns]].
You are given two strings `s` and `t`, return `true` if `s` is a **subsequence** of `t`, or `false` otherwise.

A **subsequence** of a string is a new string that is formed from the original string by deleting some (can be none) of the characters without disturbing the relative positions of the remaining characters. (i.e., `"ace"` is a subsequence of `"abcde"` while `"aec"` is not).

**Example 1:**

```java
Input: s = "node", t = "neetcode"

Output: true
```

**Example 2:**

```java
Input: s = "axc", t = "ahbgdc"

Output: false
```

**Constraints:**

- `0 <= s.length <= 100`
- `0 <= t.length <= 10,000`
- `s` and `t` consist only of lowercase English letters.

**Follow up:** Suppose there are lots of incoming `s`, say `s1, s2, ..., sk` where `k >= 1,000,000,000`, and you want to check one by one to see if `t` has its subsequence. In this scenario, how would you change your code?

**Solutions:**
```python
class Solution:

    def isSubsequence(self, s: str, t: str) -> bool:

        s_idx = 0

        s_count = len(s)

        t_idx = 0

        t_count = len(t)

        while s_idx < s_count and t_idx < t_count:

            if s[s_idx] == t[t_idx]:

                s_idx += 1

            t_idx += 1

        return s_idx >= s_count
```