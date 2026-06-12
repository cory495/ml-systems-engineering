---
Difficulty: Medium
Topics: Arrays
---

# Custom Sort String

You are given two strings `order` and `s`. All the characters of `order` are **unique** and were sorted in some custom order previously.

Permute the characters of `s` so that they match the order that `order` was sorted. More specifically, if a character `x` occurs before a character `y` in `order`, then `x` should occur before `y` in the permuted string.

Return any permutation of `s` that satisfies this property.

**Example 1:**

```java
Input: order = "xabfcg", s = "bdca"

Output: "abcd"
```

Explanation: "adbc", "dabc", "abdc" are also valid outputs.

**Example 2:**

```java
Input: order = "bfg", s = "agbfcdb"

Output: "bbfgacd"
```

**Constraints:**

- `1 <= order.length <= 26`
- `1 <= s.length <= 200`
- `order` and `s` consist of lowercase English letters.
- All the characters of `order` are **unique**.

**Solutions:**
```python
class Solution:
    def customSortString(self, order: str, s: str) -> str:
        dt = {}
        for c in order:
            dt[c] = 0
        
        for c in s:
            if dt.get(c, -1) != -1:
                dt[c] += 1
        
        ans = ""

        for c in order:
            ans += c*dt[c]
        
        for c in s:
            if dt.get(c, -1) == -1:
                ans += c
        
        return ans
```
