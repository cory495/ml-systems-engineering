---
Difficulty: Easy
Topics: Arrays
---

# Score of a String

EasyTopicsCompany Tags

You are given a string `s`. The **score** of a string is defined as the sum of the absolute difference between the **ASCII** values of adjacent characters.

Return the **score** of `s`.

**Example 1:**

```java
Input: s = "code"

Output: 24
```

Explanation: The **ASCII** values of the characters in the given string are: `'c' = 99`, `'o' = 111`, `'d' = 100`, and `'e' = 101`. The score of `s` will be: `|111 - 99| + |100 - 111| + |101 - 100|`.

**Example 2:**

```java
Input: s = "neetcode"

Output: 65
```

**Constraints:**

- `2 <= s.length <= 100`
- `s` is made up of lowercase English letters.

**Solutions:**

```python
class Solution:

    def scoreOfString(self, s: str) -> int:

        val = 0

        for i in range(1, len(s)):

            val += abs(ord(s[i-1]) - ord(s[i]))

        return val
```