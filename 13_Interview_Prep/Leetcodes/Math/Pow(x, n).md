---
Difficulty: Medium
Topics: Math
---
# Pow(x, n)

This is a part of [[LeetCode Patterns]].

`Pow(x, n)` is a mathematical function to calculate the value of `x` raised to the power of `n` (i.e., `x^n`).

Given a floating-point value `x` and an integer value `n`, implement the `myPow(x, n)` function, which calculates `x` raised to the power `n`.

You may **not** use any built-in library functions.

**Example 1:**

```java
Input: x = 2.00000, n = 5

Output: 32.00000
```

**Example 2:**

```java
Input: x = 1.10000, n = 10

Output: 2.59374
```

**Example 3:**

```java
Input: x = 2.00000, n = -3

Output: 0.12500
```

**Constraints:**

- `-100.0 < x < 100.0`
- `-1000 <= n <= 1000`
- `n` is an integer.
- If `x = 0`, then `n` will be positive.

**Solutions:**
```python
class Solution:

    def myPow(self, x: float, n: int) -> float:

        if n == 0:

            return 1

        if n == 1:

            return x

        if n < 0:

            return 1 / self.myPow(x, abs(n))

        if n % 2 == 0:

            return self.myPow(x*x, n//2)

        else:

            return self.myPow(x*x, n//2)*x
```