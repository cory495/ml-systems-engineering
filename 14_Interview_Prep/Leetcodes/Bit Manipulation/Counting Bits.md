---
Difficulty: Easy
Topics: Bit Manipulation
---

# Counting Bits

Given an integer `n`, count the number of `1`'s in the binary representation of every number in the range `[0, n]`.

Return an array `output` where `output[i]` is the number of `1`'s in the binary representation of `i`.

**Example 1:**

```java
Input: n = 4

Output: [0,1,1,2,1]
```

Explanation:  
0 --> 0  
1 --> 1  
2 --> 10  
3 --> 11  
4 --> 100

**Constraints:**

- `0 <= n <= 1000`
**Solutions:**
```python
class Solution:

    def countBits(self, n: int) -> List[int]:

        if n == 0:

            return [0]

        nums = [0]*(n+1)

        nums[1] = 1

        for i in range(2, n+1):

            nums[i] = nums[i>>1] + (i&1)

        return nums
```