---
Difficulty: Hard
Topics: Stacks
---

# Largest Rectangle in Histogram

This is a part of [[LeetCode Patterns]].

You are given an array of integers `heights` where `heights[i]` represents the height of a bar. The width of each bar is `1`.

Return the area of the largest rectangle that can be formed among the bars.

Note: This chart is known as a [histogram](https://en.wikipedia.org/wiki/Histogram).

**Example 1:**

```java
Input: heights = [7,1,7,2,2,4]

Output: 8
```

**Example 2:**

```java
Input: heights = [1,3,7]

Output: 7
```

**Constraints:**

- `1 <= heights.length <= 1000`.
- `0 <= heights[i] <= 1000`

**Solutions:**

```python
class Solution:

    def largestRectangleArea(self, heights: List[int]) -> int:

        max_area = 0

        n = len(heights)

        for i in range(n):

            left = right = i

            while left-1>=0 and heights[left-1]>=heights[i]:

                left -= 1

            while right+1<n and heights[right+1]>=heights[i]:

                right += 1

            cur_area = heights[i]*(right-left+1)

            max_area = max(max_area, cur_area)

        return max_area
```

```python
class Solution:

    def largestRectangleArea(self, heights: List[int]) -> int:

        stack = []

        max_area = 0

  

        for i, h in enumerate(heights):

            start = i

            while stack and stack[-1][1] > h:

                index, height = stack.pop()

                max_area = max(max_area, height * (i - index))

                start = index

  

            stack.append((start, h))

        n = len(heights)

  

        while stack:

            index, height = stack.pop()

            max_area = max(max_area, height * (n - index))

  

        return max_area
```