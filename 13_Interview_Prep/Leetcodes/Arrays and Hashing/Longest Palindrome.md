---
Difficulty: Easy
Topics: Arrays
---
# Longest Palindrome

This is a part of [[LeetCode Patterns]].

You are given a string `s` which consists of lowercase or uppercase letters, return the length of the **longest** palindrome that can be built with those letters.

Letters are **case sensitive**, for example, `"Aa"` is not considered a palindrome.

**Example 1:**

```java
Input: s = "abccccdd"

Output: 7
```

Explanation: One longest palindrome that can be built is "dccaccd", whose length is 7.

**Example 2:**

```java
Input: s = "a"

Output: 1
```

Explanation: The longest palindrome that can be built is "a", whose length is 1.

**Constraints:**

- `1 <= s.length <= 2,000`
- `s` consists of lowercase **and/or** uppercase English letters only.

**Solutions:**

```python
class Solution:

    def longestPalindrome(self, s: str) -> int:

        counts = Counter(s)

        res = 0

        for v in counts.values():

            if v % 2 == 0:

                res += v

            elif v - 1 > 0:

                res += v-1

        if len(s) > res:

            res += 1

        return res
```

```python
class Solution:

    def longestPalindrome(self, s: str) -> int:

        counts = Counter(s)

        res = 0

        for v in counts.values():

            res += v - (v % 2)

        if len(s) > res:

            res += 1

        return res
```