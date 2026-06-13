---
Difficulty: Easy
Topics: Arrays
---
# Isomorphic Strings

This is a part of [[LeetCode Patterns]].

You are given two strings `s` and `t`, determine if they are **isomorphic**.

Two strings `s` and `t` are isomorphic if the characters in `s` can be replaced to get `t`.

All occurrences of a character must be replaced with another character while preserving the order of characters. No two characters may map to the same character, but a character may map to itself.

**Example 1:**

```java
Input: s = "egg", t = "add"

Output: true
```

Explanation: The strings s and t can be made identical by:

- Mapping 'e' to 'a'.
- Mapping 'g' to 'd'.

**Example 2:**

```java
Input: s = "foo", t = "bar"

Output: false
```

Explanation: The strings s and t can not be made identical as 'o' needs to be mapped to both 'a' and 'r'.

**Example 3:**

```java
Input: s = "paper", t = "title"

Output: true
```

**Constraints:**

- `0 <= s.length == t.length <= 50,000`
- `s` and `t` consist of any valid ascii character.

**Solutions:**

```python
class Solution:

    def isIsomorphic(self, s: str, t: str) -> bool:

        dt = {}

        n, m = len(s), len(t)

        if n != m:

            return False

  

        for i in range(n):

            if dt.get(s[i], -1) == -1 and t[i] not in dt.values():

                dt[s[i]] = t[i]

            elif t[i] in dt.values() and s[i] not in dt:

                return False

            elif dt[s[i]] != t[i]:

                return False

        return True
```

```python
class Solution:

    def isIsomorphic(self, s: str, t: str) -> bool:

        if len(s) != len(t):

            return False

  

        s_to_t = {}

        t_to_s = {}

  

        for a, b in zip(s, t):

            if a in s_to_t and s_to_t[a] != b:

                return False

            if b in t_to_s and t_to_s[b] != a:

                return False

  

            s_to_t[a] = b

            t_to_s[b] = a

  

        return True
```