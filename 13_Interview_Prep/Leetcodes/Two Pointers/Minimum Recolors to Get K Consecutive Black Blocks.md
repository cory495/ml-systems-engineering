---
Difficulty: Easy
Topics: Two Pointers
---
# Minimum Recolors to Get K Consecutive Black Blocks

This is a part of [[LeetCode Patterns]].

You are given a **0-indexed** string blocks of length `n`, where `blocks[i]` is either `'W'` or `'B'`, representing the color of the `ith` block. The characters `'W'` and `'B'` denote the colors white and black, respectively.

You are also given an integer `k`, which is the desired number of **consecutive** black blocks.

In one operation, you can recolor a white block such that it becomes a black block.

Return the **minimum** number of operations needed such that there is **at least one** occurrence of `k` consecutive black blocks.

**Example 1:**

```java
Input: blocks = "WBBWWBBWBW", k = 7

Output: 3
```

Explanation: Recolor the 0th, 3rd, and 4th blocks to get 7 consecutive black blocks.

**Example 2:**

```java
Input: blocks = "BWWWBB", k = 6

Output: 3
```

Explanation: Recolor all the white blocks with black.

**Constraints:**

- `1 <= k <= blocks.length <= 100`
- `blocks[i]` is either `'W'` or `'B'`.

**Solutions:**

```python
class Solution:
    def minimumRecolors(self, blocks: str, k: int) -> int:
        count = 0
        min_change = float('inf')
        
        left = 0
        for right in range(len(blocks)):
            if blocks[right] == 'W':
                count += 1
            if right-left+1 > k:
                if blocks[left] == 'W':
                    count -= 1
                left += 1
            if right-left+1 == k:
                min_change = min(min_change, count)
            right += 1
        return min_change
```
