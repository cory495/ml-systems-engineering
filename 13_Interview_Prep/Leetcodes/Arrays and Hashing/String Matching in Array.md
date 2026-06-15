---
Difficulty: Easy
Topics: Arrays
---

# String Matching in an Array

This is a part of [[LeetCode Patterns]].

You are given an array of string `words`, return all strings in `words` that are a **substring** of another word. You can return the answer in **any order**.

Note: A **substring** is a contiguous **non-empty** sequence of characters within a string.

**Example 1:**

```java
Input: words = ["mass","as","hero","superhero"]

Output: ["as","hero"]
```

Explanation: "as" is substring of "mass" and "hero" is substring of "superhero". ["hero","as"] is also a valid answer.

**Example 2:**

```java
Input: words = ["neetcode","neeet","neet","code"]

Output: ["neet","code"]
```

Explanation: "neet" and "code" are substrings of "neetcode".

**Example 3:**

```java
Input: words = ["blue","green","bu"]

Output: []
```

Explanation: No string of words is substring of another string.

**Constraints:**

- `1 <= words.length <= 100`
- `1 <= words[i].length <= 30`
- `words[i]` contains only lowercase English letters.
- All the strings of `words` are **unique**.

**Solutions:**
```python
class Solution:

    def stringMatching(self, words: List[str]) -> List[str]:

        n = len(words)

        res = set()

        for i in range(n):

            for j in range(n):

                if i != j:

                    if words[i] in words[j]:

                        res.add(words[i])

        return list(res)
```

```python
class Solution:

    def stringMatching(self, words: List[str]) -> List[str]:

        n = len(words)

        res = []

        prefix = [''] * n

        postfix = [''] * n

        for i in range(1, n):

            prefix[i] = prefix[i - 1] + '#' + words[i - 1]

        for i in reversed(range(n-1)):

            postfix[i] = postfix[i + 1] + '#' + words[i + 1]

        for i in range(n):

            if words[i] in prefix[i] or words[i] in postfix[i]:

                res.append(words[i])

        return res
```

```python
class Solution:

    def stringMatching(self, words: List[str]) -> List[str]:

        words.sort(key=len)

        res = set()

        for i in range(len(words)):

            for j in range(i + 1, len(words)):

                if words[i] in words[j]:

                    res.add(words[i])

                    break

        return list(res)
```