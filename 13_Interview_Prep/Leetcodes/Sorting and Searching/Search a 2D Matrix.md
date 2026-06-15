---
Difficulty: Medium
Topics: Sorting
---

# Search a 2D Matrix

This is a part of [[LeetCode Patterns]].

You are given an `m x n` 2-D integer array `matrix` and an integer `target`.

- Each row in `matrix` is sorted in _non-decreasing_ order.
- The first integer of every row is greater than the last integer of the previous row.

Return `true` if `target` exists within `matrix` or `false` otherwise.

Can you write a solution that runs in `O(log(m * n))` time?

**Example 1:**

![](https://imagedelivery.net/CLfkmk9Wzy8_9HRyug4EVA/7ca61f56-00d4-4fa0-26cf-56809028ac00/public)

```java
Input: matrix = [[1,2,4,8],[10,11,12,13],[14,20,30,40]], target = 10

Output: true
```

**Example 2:**

![](https://imagedelivery.net/CLfkmk9Wzy8_9HRyug4EVA/f25f2085-ce04-4447-9cee-f0a66c32a300/public)

```java
Input: matrix = [[1,2,4,8],[10,11,12,13],[14,20,30,40]], target = 15

Output: false
```

**Constraints:**

- `m == matrix.length`
- `n == matrix[i].length`
- `1 <= m, n <= 100`
- `-10000 <= matrix[i][j], target <= 10000`

**Solutions:**

```python
class Solution:

    def searchMatrix(self, matrix: List[List[int]], target: int) -> bool:

        count = len(matrix) * len(matrix[0])

        COL = len(matrix[0])

        ROW = len(matrix)

        left, right = 0, count-1

  

        while left <= right:

            mid = (left+right)//2

            row = math.floor(mid / COL)

            col = mid - row * COL

  

            if matrix[row][col] == target:

                return True

            elif matrix[row][col] > target:

                right = mid - 1

            else:

                left = mid + 1

        return False
```