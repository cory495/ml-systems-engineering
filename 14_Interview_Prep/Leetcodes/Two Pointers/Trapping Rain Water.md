---
Difficulty: Hard
Topics: Two Pointers
---
# Trapping Rain Water


You are given an array of non-negative integers `height` which represent an elevation map. Each value `height[i]` represents the height of a bar, which has a width of `1`.

Return the maximum area of water that can be trapped between the bars.

**Example 1:**

![](https://imagedelivery.net/CLfkmk9Wzy8_9HRyug4EVA/0c25cb81-1095-4382-fff2-6ef77c1fd100/public)

```java
Input: height = [0,2,0,3,1,0,1,3,2,1]

Output: 9
```

**Constraints:**

- `1 <= height.length <= 1000`
- `0 <= height[i] <= 1000`

**Solutions:**

```python
class Solution:

    def trap(self, height: List[int]) -> int:

        n = len(height)

        prefix = [0] * n

        prefix[0] = 0

        for i in range(1, n):

            prefix[i] = max(prefix[i-1], height[i-1])

        postfix = [0] * n

        postfix[n-1] = 0

        for i in reversed(range(0, n-1)):

            postfix[i] = max(postfix[i+1], height[i+1])

        amount = 0

        for i in range(n):

            h = min(prefix[i], postfix[i])

            amount += max(h-height[i], 0)

        return amount
```