---
Difficulty: Easy
Topics: Bit Manipulation
Created: 2026-06-01
Updated: 2026-06-26
tags:
  - interview
  - programming
Type: Interview
---
# Reverse Bits

This is a part of [[LeetCode Patterns]].

Given a 32-bit unsigned integer `n`, reverse the bits of the binary representation of `n` and return the result.

**Example 1:**

```java
Input: n = 00000000000000000000000000010101

Output:    2818572288 (10101000000000000000000000000000)
```

Explanation: Reversing `00000000000000000000000000010101`, which represents the unsigned integer `21`, gives us `10101000000000000000000000000000` which represents the unsigned integer `2818572288`.

**Solutions:**
```python
class Solution:

    def reverseBits(self, n: int) -> int:

        res = 0

        for i in range(32):

            bit = (n >> i) & 1

            res += (bit << 31 - i)

        return res
```