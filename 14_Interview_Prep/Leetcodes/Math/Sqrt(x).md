---
Difficulty: Easy
Topics: Math
---


# Sqrt(x)

This is a part of [[LeetCode Patterns]].

You are given a non-negative integer `x`, return the **square root** of `x` **rounded down** to the nearest integer. The returned integer should be non-negative as well.

You **must not use** any built-in exponent function or operator.

- For example, do not use `pow(x, 0.5)` in `c++` or `x ** 0.5` in `python`.

**Example 1:**

```java
Input: x = 9

Output: 3
```

**Example 2:**

```java
Input: x = 13

Output: 3
```

**Constraints:**

- `0 <= x <= ((2^31)-1)`

**Solutions:**

```python
class Solution:

    def mySqrt(self, x: int) -> int:

        left, right = 0, x

  

        while left <= right:

            mid = (left + right) // 2

            if mid*mid > x:

                right = mid - 1

            else:

                left = mid + 1

        return left - 1
```

```python
class Solution:

    def mySqrt(self, x: int) -> int:

        if x == 0:

            return 0

  

        r = x

        while r * r > x:

            r = (r + x // r) // 2

  

        return r
```