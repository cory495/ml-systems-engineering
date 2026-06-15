---
Difficulty: Easy
Topics: Two Pointers
---
# Find First Palindromic String in Array

This is a part of [[LeetCode Patterns]].

Given an array of strings `words`, return _the first **palindromic** string in the array_. If there is no such string, return _an **empty string**_ `""`.

A string is **palindromic** if it reads the same forward and backward.

**Example 1:**

**Input:** words = ["abc","car","ada","racecar","cool"]
**Output:** "ada"
**Explanation:** The first string that is palindromic is "ada".
Note that "racecar" is also palindromic, but it is not the first.

**Example 2:**

**Input:** words = ["notapalindrome","racecar"]
**Output:** "racecar"
**Explanation:** The first and only string that is palindromic is "racecar".

**Example 3:**

**Input:** words = ["def","ghi"]
**Output:** ""
**Explanation:** There are no palindromic strings, so the empty string is returned.

**Constraints:**

- `1 <= words.length <= 100`
- `1 <= words[i].length <= 100`
- `words[i]` consists only of lowercase English letters

**Solutions:**

```python
class Solution:

    def firstPalindrome(self, words: List[str]) -> str:

        for s in words:

            n = len(s)

            i = 0

            is_pal = True

            while i <= n // 2:

                if s[i] != s[n-i-1]:

                    is_pal = False

                    break

                i += 1

            if is_pal:

                return s

        return ""
```

```python
class Solution:
    def firstPalindrome(self, words: List[str]) -> str:
        for s in words:
            n = len(s)

            for i in range(n // 2):
                if s[i] != s[n - i - 1]:
                    break
            else:
                return s

        return ""
```

```python
class Solution:

    def firstPalindrome(self, words: List[str]) -> str:

        for s in words:

            if s == s[::-1]:

                return s

        return ""
```