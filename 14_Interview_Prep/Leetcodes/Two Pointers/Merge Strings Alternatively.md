---
Difficulty: Easy
Topics: Two Pointers
---
# Merge Strings Alternately

This is a part of [[LeetCode Patterns]].

You are given two strings, `word1` and `word2`. Construct a new string by merging them in **alternating** order, starting with `word1` — take one character from `word1`, then one from `word2`, and repeat this process.

If one string is longer than the other, append the remaining characters from the longer string to the end of the merged result.

Return the final merged string.

**Example 1:**

```java
Input: word1 = "abc", word2 = "xyz"

Output: "axbycz"
```

**Example 2:**

```java
Input: word1 = "ab", word2 = "abbxxc"

Output: "aabbbxxc"
```

**Constraints:**

- `1 <= word1.length, word2.length <= 100`
- `word1` and `word2` consist of lowercase English letters.

**Solutions:**

```python
class Solution:
    def mergeAlternately(self, word1: str, word2: str) -> str:
        n, m = len(word1), len(word2)
        i = 0
        res = ""
        while i < min(n, m):
            res += word1[i] + word2[i]
            i += 1
        res += word1[i:] + word2[i:]
        return res
```

```python
class Solution:
    def mergeAlternately(self, word1: str, word2: str) -> str:
        n, m = len(word1), len(word2)
        i = 0
        res = []
        while i < min(n, m):
            res.append(word1[i])
            res.append(word2[i])
            i += 1
        res.extend(word1[i:])
        res.extend(word2[i:])
        return ''.join(res)
```
```python
class Solution:
    def mergeAlternately(self, word1: str, word2: str) -> str:
        result = []
        for i in range(min(len(word1), len(word2))):
            result.extend([word1[i], word2[i]])
        
        return ''.join(result) + word1[i+1:] + word2[i+1:]
```
