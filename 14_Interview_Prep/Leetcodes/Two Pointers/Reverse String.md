---
Difficulty: Easy
Topics: Two Pointers
---
# Reverse String

This is a part of [[LeetCode Patterns]].

You are given an array of characters which represents a string `s`. Write a function which reverses a string.

You must do this by modifying the input array in-place with `O(1)` extra memory.

**Example 1:**

```java
Input: s = ["n","e","e","t"]

Output: ["t","e","e","n"]
```

**Example 2:**

```java
Input: s = ["r","a","c","e","c","a","r"]

Output: ["r","a","c","e","c","a","r"]
```

**Constraints:**

- `1 <= s.length < 100,000`
- `s[i]` is a [printable ascii character](https://en.wikipedia.org/wiki/ASCII#Printable_characters).

**Solutions:**
```python
class Solution:

    def reverseString(self, s: List[str]) -> None:

        """

        Do not return anything, modify s in-place instead.

        """

        n = len(s)

        for i in range(n // 2):

            s[i], s[n-i-1] = s[n-i-1], s[i]

        return s
```

```python
class Solution:

    def reverseString(self, s: List[str]) -> None:

        s[:] = s[::-1]
```