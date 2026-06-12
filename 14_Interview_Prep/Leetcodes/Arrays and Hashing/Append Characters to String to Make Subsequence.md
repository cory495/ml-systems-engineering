---
Difficulty: Medium
Topics: Arrays
---

# Append Characters to String to Make Subsequence

This is a part of [[LeetCode Patterns]].
You are given two strings `s` and `t` consisting of only lowercase English letters.

Return the minimum number of characters that need to be appended to the end of `s` so that `t` becomes a subsequence of `s`.

A **subsequence** is a string that can be derived from another string by deleting some or no characters without changing the order of the remaining characters.

**Example 1:**

```java
Input: s = "coaching", t = "coding"

Output: 4
```

Explanation: Append the characters `"ding"` to the end of `s` so that `s = "coachingding"`.  
Now, `t` is a subsequence of `s` (**co**aching**ding**).  
It can be shown that appending any `3` characters to the end of `s` will never make `t` a subsequence.

**Example 2:**

```java
Input: s = "abcde", t = "a"

Output: 0
```

Explanation: `t` is already a subsequence of `s` ("**a**bcde").

**Example 3:**

```java
Input: s = "z", t = "abcde"

Output: 5
```

Explanation: Append the characters `"abcde"` to the end of `s` so that `s = "zabcde"`.  
Now, `t` is a subsequence of `s` (z**abcde**).  
It can be shown that appending any `4` characters to the end of `s` will never make `t` a subsequence.

**Constraints:**

- `1 <= s.length, t.length <= 100,000`
- `s` and `t` consist of lowercase English letters.

**Solutions:**

```python
class Solution:

    def appendCharacters(self, s: str, t: str) -> int:

        s_idx = 0

        s_count = len(s)

        t_idx = 0

        t_count = len(t)

        while s_idx < s_count and t_idx < t_count:

            if t[t_idx] == s[s_idx]:

                t_idx += 1

            s_idx += 1

        return t_count - t_idx
```