---
Difficulty: Easy
Topics: Arrays
---

# Pascal's Triangle

This is a part of [[LeetCode Patterns]].

You are given an integer `numRows`, return the first numRows of **Pascal's triangle**.

In **Pascal's triangle**, each number is the sum of the two numbers directly above it as shown:

![](https://upload.wikimedia.org/wikipedia/commons/0/0d/PascalTriangleAnimated2.gif)

**Example 1:**

```java
Input: numRows = 5

Output: [[1],[1,1],[1,2,1],[1,3,3,1],[1,4,6,4,1]]
```

**Example 2:**

```java
Input: numRows = 1

Output: [[1]]
```

**Constraints:**

- `1 <= numRows <= 30`

**Solutions:**

```python
class Solution:

    def generate(self, numRows: int) -> List[List[int]]:

        res = [[1]]

        for num in range(1, numRows):

            add = [1]

            j = 0

            while j+1 < num:

                add.append(res[num-1][j] + res[num-1][j+1])

                j += 1

            add.append(1)

            res.append(add)

        return res
```