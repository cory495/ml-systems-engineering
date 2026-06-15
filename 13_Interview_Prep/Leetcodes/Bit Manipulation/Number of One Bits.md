---
Difficulty: Easy
Topics: Bit Manipulation
---

# Number of 1 Bits

This is a part of [[LeetCode Patterns]].

You are given an unsigned integer `n`. Return the number of `1` bits in its binary representation.

You may assume `n` is a non-negative integer which fits within 32-bits.

**Example 1:**

```java
Input: n = 00000000000000000000000000010111

Output: 4
```

**Example 2:**

```java
Input: n = 01111111111111111111111111111101

Output: 30
```

**Solutions:**
```python
class Solution:

    def hammingWeight(self, n: int) -> int:

        ans = 0

        while n > 0:

            ans += n % 2

            n = n >> 1

        return ans
```

The first solution is the naive approach of checking each bit. The bottom approach checks the furthest one bit.
```python
class Solution:

    def hammingWeight(self, n: int) -> int:

        count = 0

        while n:

            n &= (n - 1)

            count += 1

        return count
```