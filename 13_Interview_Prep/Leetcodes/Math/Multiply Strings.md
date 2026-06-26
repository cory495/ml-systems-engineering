---
Difficulty: Medium
Topics: Math
Created: 2026-06-01
Updated: 2026-06-26
tags:
  - interview
  - programming
Type: Interview
---
# Multiply Strings

This is a part of [[LeetCode Patterns]].

You are given two strings `num1` and `num2` that represent non-negative integers.

Return the product of `num1` and `num2` in the form of a string.

Assume that neither `num1` nor `num2` contain any leading zero, unless they are the number `0` itself.

**Note**: You can not use any built-in library to convert the inputs directly into integers.

**Example 1:**

```java
Input: num1 = "3", num2 = "4"

Output: "12"
```

**Example 2:**

```java
Input: num1 = "111", num2 = "222"

Output: "24642"
```

**Constraints:**

- `1 <= num1.length, num2.length <= 200`
- `num1` and `num2` consist of digits only.

**Solutions:**

```python
class Solution:

    def multiply(self, num1: str, num2: str) -> str:

        def convertToNum(num):

            res = 0

            for c in num:

                res = res * 10 + ord(c) - ord('0')

            return res

        return str(convertToNum(num1) * convertToNum(num2))
```

```python
class Solution:

    def multiply(self, num1: str, num2: str) -> str:

        if num1 == "0" or num2 == "0":

            return "0"

  

        m, n = len(num1), len(num2)

        res = [0] * (m + n)

  

        num1, num2 = num1[::-1], num2[::-1]

  

        for i in range(m):

            for j in range(n):

                digit = (ord(num1[i]) - ord('0')) * (ord(num2[j]) - ord('0'))

                res[i + j] += digit

                res[i + j + 1] += res[i + j] // 10

                res[i + j] %= 10

  

        while len(res) > 1 and res[-1] == 0:

            res.pop()

  

        return ''.join(map(str, reversed(res)))
```