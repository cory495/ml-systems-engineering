---
Difficulty: Easy
Topics: Arrays
---
# Maximum Difference Between Even and Odd Frequency I

This is a part of [[LeetCode Patterns]].

You are given a string `s` consisting of lowercase English letters.

Your task is to find the **maximum difference** `diff = freq(a1) - freq(a2)` between the frequency of characters `a1` and `a2` in the string such that:

- `a1` has an **odd frequency** in the string.
- `a2` has an **even frequency** in the string.

Return this **maximum** difference.

**Example 1:**

```java
Input: s = "aaaaabbc"

Output: 3
```

Explanation:

- The character 'a' has an odd frequency of 5, and 'b' has an even frequency of 2.
- The maximum difference is 5 - 2 = 3.

**Example 2:**

```java
Input: s = "abcabcab"

Output: 1
```

Explanation:

- The character 'a' has an odd frequency of 3, and 'c' has an even frequency of 2.
- The maximum difference is 3 - 2 = 1.

**Constraints:**

- `3 <= s.length <= 100`
- `s` consists only of lowercase English letters.
- `s` contains at least one character with an odd frequency and one with an even frequency.

**Solutions:**

```python
class Solution:

    def maxDifference(self, s: str) -> int:

        dt = {}

  

        for c in s:

            dt[c] = dt.get(c, 0) + 1

        odd, even = float('-inf'), float('inf')

        for k, v in dt.items():

            if v % 2 == 1:

                odd = max(odd, v)

            else:

                even = min(even, v)

        return odd - even
```

```python
class Solution:

    def maxDifference(self, s: str) -> int:

        odd = float('-inf')

        even = float('inf')

  

        for freq in Counter(s).values():

            if freq & 1:

                odd = max(odd, freq)

            else:

                even = min(even, freq)

  

        return odd - even
```
