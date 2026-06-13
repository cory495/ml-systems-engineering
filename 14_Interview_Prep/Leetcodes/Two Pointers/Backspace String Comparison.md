---
Difficulty: Easy
Topics: Two Pointers
---

# Backspace String Comparison

This is a part of [[LeetCode Patterns]].

Given two strings `s` and `t`, return `true` _if they are equal when both are typed into empty text editors_. `'#'` means a backspace character.

Note that after backspacing an empty text, the text will continue empty.

**Example 1:**

**Input:** s = "ab#c", t = "ad#c"
**Output:** true
**Explanation:** Both s and t become "ac".

**Example 2:**

**Input:** s = "ab##", t = "c#d#"
**Output:** true
**Explanation:** Both s and t become "".

**Example 3:**

**Input:** s = "a#c", t = "b"
**Output:** false
**Explanation:** s becomes "c" while t becomes "b".

**Constraints:**

- `1 <= s.length, t.length <= 200`
- `s` and `t` only contain lowercase letters and `'#'` characters.

**Follow up:** Can you solve it in `O(n)` time and `O(1)` space?

**Solutions:**

```python
class Solution(object):

    def backspaceCompare(self, S, T):

        def build(S):

            ans = []

            for c in S:

                if c != '#':

                    ans.append(c)

                elif ans:

                    ans.pop()

            return "".join(ans)

        return build(S) == build(T)
```

```python
class Solution:

    def backspaceCompare(self, s: str, t: str) -> bool:

        i, j = len(s) - 1, len(t) - 1

  

        while i >= 0 or j >= 0:

            # Find next valid character in s

            skip = 0

            while i >= 0:

                if s[i] == '#':

                    skip += 1

                elif skip:

                    skip -= 1

                else:

                    break

                i -= 1

  

            # Find next valid character in t

            skip = 0

            while j >= 0:

                if t[j] == '#':

                    skip += 1

                elif skip:

                    skip -= 1

                else:

                    break

                j -= 1

  

            # Compare characters

            if i >= 0 and j >= 0:

                if s[i] != t[j]:

                    return False

            elif i >= 0 or j >= 0:

                return False

  

            i -= 1

            j -= 1

  

        return True
```