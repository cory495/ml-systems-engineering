---
Difficulty: Medium
Topics: Bit Manipulation
Type: Interview
Created: 2026-06-28
Updated: 2026-06-28
tags:
  - intervals
  - algorithms
  - programming
  - bit-manipulation
---
# Sum of Two Integers

**Solutions:**

```python
class Solution:

    def getSum(self, a: int, b: int) -> int:

        MASK = 0xFFFFFFFF

        MAX = 0x7FFFFFFF

  

        while b:

            a, b = (a ^ b) & MASK, ((a & b) << 1) & MASK

  

        # Convert back from unsigned to signed

        return a if a <= MAX else ~(a ^ MASK)
```