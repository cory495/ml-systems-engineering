---
Difficulty: Medium
Topics: Two Pointers
---

# Container With Most Water

You are given an integer array `heights` where `heights[i]` represents the height of the ithith bar.

You may choose any two bars to form a container. Return the _maximum_ amount of water a container can store.

**Example 1:**

![](https://imagedelivery.net/CLfkmk9Wzy8_9HRyug4EVA/77f004c6-e773-4e63-7b99-a2309303c700/public)

```java
Input: height = [1,7,2,5,4,7,3,6]

Output: 36
```

**Example 2:**

```java
Input: height = [2,2,2]

Output: 4
```

**Constraints:**

- `2 <= height.length <= 1000`
- `0 <= height[i] <= 1000`

**Solutions:**
```python
class Solution:
    def maxArea(self, heights: List[int]) -> int:
        left, right = 0, len(heights) - 1 
        max_area = 0
        
        while left < right:
            width = right - left
            height = min(heights[left], heights[right])
            current_area = width * height
            max_area = max(max_area, current_area)
            
            if heights[left] < heights[right]:
                left += 1
            else:
                right -= 1
                
        return max_area
```
