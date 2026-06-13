---
Difficulty: Easy
Topics: Arrays
---
# Longest Common Prefix

This is a part of [[LeetCode Patterns]].

You are given an array of strings `strs`. Return the **longest common prefix** of all the strings.

If there is no longest common prefix, return an empty string `""`.

**Example 1:**

```java
Input: strs = ["bat","bag","bank","band"]

Output: "ba"
```

**Example 2:**

```java
Input: strs = ["dance","dag","danger","damage"]

Output: "da"
```

**Example 3:**

```java
Input: strs = ["neet","feet"]

Output: ""
```

**Constraints:**

- `1 <= strs.length <= 200`
- `0 <= strs[i].length <= 200`
- `strs[i]` is made up of lowercase English letters if it is non-empty.

**Solutions:**

```python
class Solution:

    def longestCommonPrefix(self, strs: List[str]) -> str:

        res = strs[0]

        for i in range(1, len(strs)):

            on = 0

            while on < len(res) and on < len(strs[i]) and strs[i][on] == res[on]:

                on += 1

            res = res[:on]

        return res
```

```python
class Solution:

    def longestCommonPrefix(self, strs: List[str]) -> str:

        for i, ch in enumerate(strs[0]):

            for s in strs[1:]:

                if i >= len(s) or s[i] != ch:

                    return strs[0][:i]

  

        return strs[0]
```