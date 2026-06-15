---
Difficulty: Easy
Topics: Arrays
---

# Replace Elements With Greatest Element On Right Side

This is a part of [[LeetCode Patterns]].

You are given an array `arr`, replace every element in that array with the greatest element among the elements to its right, and replace the last element with `-1`.

After doing so, return the array.

**Example 1:**

```java
Input: arr = [2,4,5,3,1,2]

Output: [5,5,3,2,2,-1]
```

**Example 2:**

```java
Input: arr = [3,3]

Output: [3,-1]
```

**Constraints:**

- `1 <= arr.length <= 10,000`
- `1 <= arr[i] <= 100,000`

**Solutions:**

```python
class Solution:

    def replaceElements(self, arr: List[int]) -> List[int]:

        n = len(arr)

        ans = [-1] * n

        for i in reversed(range(n-1)):

            ans[i] = max(ans[i+1], arr[i+1])

        return ans
```