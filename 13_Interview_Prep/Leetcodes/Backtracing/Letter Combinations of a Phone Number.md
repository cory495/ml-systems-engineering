---
Difficulty: Medium
Topics: Backtracing
Created: 2026-06-01
Updated: 2026-06-26
tags:
  - interview
  - programming
Type: Interview
---
# Letter Combinations of a Phone Number

This is a part of [[LeetCode Patterns]].

You are given a string `digits` made up of digits from `2` through `9` inclusive.

Each digit (not including 1) is mapped to a set of characters as shown below:

A digit could represent any one of the characters it maps to.

Return all possible letter combinations that `digits` could represent. You may return the answer in **any order**.

![Phone keypad letter mapping](https://imagedelivery.net/CLfkmk9Wzy8_9HRyug4EVA/d5eb2098-bd7f-47a1-554a-ad77a39f3100/public)

**Example 1:**

```java
Input: digits = "34"

Output: ["dg","dh","di","eg","eh","ei","fg","fh","fi"]
```

**Example 2:**

```java
Input: digits = ""

Output: []
```

**Constraints:**

- `0 <= digits.length <= 4`
- `2 <= digits[i] <= 9`

**Solutions:**

```python
class Solution:
    def letterCombinations(self, digits: str) -> List[str]:
        dt = {
            '2': ['a', 'b', 'c'],
            '3': ['d', 'e', 'f'],
            '4': ['g', 'h', 'i'],
            '5': ['j', 'k', 'l'],
            '6': ['m', 'n', 'o'],
            '7': ['p', 'q', 'r', 's'],
            '8': ['t', 'u', 'v'],
            '9': ['w', 'x', 'y', 'z']
        }
        if len(digits) < 1:
            return []
        res = dt[digits[0]]

        for c in digits[1:]:
            replace = []
            for char in dt[c]:
                for i in range(len(res)):
                    replace.append(res[i] + char)
            res = replace
        return res
```

```python
class Solution:
    def letterCombinations(self, digits: str) -> List[str]:
        dt = {
            '2': ['a', 'b', 'c'],
            '3': ['d', 'e', 'f'],
            '4': ['g', 'h', 'i'],
            '5': ['j', 'k', 'l'],
            '6': ['m', 'n', 'o'],
            '7': ['p', 'q', 'r', 's'],
            '8': ['t', 'u', 'v'],
            '9': ['w', 'x', 'y', 'z']
        }
        if len(digits) == 0:
            return []
        res = []

        def backtrace(i=0, cur=""):
            if len(digits) == len(cur):
                res.append(cur)
                return
            
            for c in dt[digits[i]]:
                backtrace(i+1, cur+c)
        
        backtrace()
        return res
```
