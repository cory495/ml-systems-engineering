---
Difficulty: Medium
Topics: Arrays
---
# Range Sum Query 2D Immutable

This is a part of [[LeetCode Patterns]].

You are given a 2D matrix `matrix`, handle multiple queries of the following type:

- Calculate the `sum` of the elements of `matrix` inside the rectangle defined by its **upper left corner** `(row1, col1)` and **lower right corner** `(row2, col2)`.

Implement the `NumMatrix` class:

- `NumMatrix(int[][] matrix)` Initializes the object with the integer matrix `matrix`.
- `int sumRegion(int row1, int col1, int row2, int col2)` Returns the **sum** of the elements of `matrix` inside the rectangle defined by its **upper left corner** `(row1, col1)` and **lower right corner** `(row2, col2)`.  
    You must design an algorithm where `sumRegion` works on `O(1)` time complexity.

**Example 1:**

![](https://imagedelivery.net/CLfkmk9Wzy8_9HRyug4EVA/fde9e326-d568-4764-e646-d2069c3af000/public)

```java
Input: ["NumMatrix", "sumRegion", "sumRegion", "sumRegion"]
[[[[3, 0, 1, 4, 2], [5, 6, 3, 2, 1], [1, 2, 0, 1, 5], [4, 1, 0, 1, 7], [1, 0, 3, 0, 5]]], [2, 1, 4, 3], [1, 1, 2, 2], [1, 2, 2, 4]]

Output: [null, 8, 11, 12]
```

Explanation:

```java
NumMatrix numMatrix = new NumMatrix([[3, 0, 1, 4, 2], [5, 6, 3, 2, 1], [1, 2, 0, 1, 5], [4, 1, 0, 1, 7], [1, 0, 3, 0, 5]]);
numMatrix.sumRegion(2, 1, 4, 3); // return 8 (i.e sum of the red rectangle)
numMatrix.sumRegion(1, 1, 2, 2); // return 11 (i.e sum of the green rectangle)
numMatrix.sumRegion(1, 2, 2, 4); // return 12 (i.e sum of the blue rectangle)
```

**Constraints:**

- `m == matrix.length`
- `n == matrix[i].length`
- `1 <= m, n <= 200`
- `-10,000 <= matrix[i][j] <= 10,000`
- `0 <= row1 <= row2 < m`
- `0 <= col1 <= col2 < n`
- At most `10,000` calls will be made to `sumRegion`.

**Solutions:**

```python
class NumMatrix:

    def __init__(self, matrix: list[list[int]]):
        self.matrix = matrix

    def sumRegion(self, row1: int, col1: int, row2: int, col2: int) -> int:
        res = 0
        for r in range(row1, row2 + 1):
            for c in range(col1, col2 + 1):
                res += self.matrix[r][c]
        return res
```

```python
class NumMatrix:

    def __init__(self, matrix: list[list[int]]):
        ROWS, COLS = len(matrix), len(matrix[0])
        self.sumMat = [[0] * (COLS + 1) for _ in range(ROWS + 1)]

        for r in range(ROWS):
            prefix = 0
            for c in range(COLS):
                prefix += matrix[r][c]
                above = self.sumMat[r][c + 1]
                self.sumMat[r + 1][c + 1] = prefix + above

    def sumRegion(self, row1: int, col1: int, row2: int, col2: int) -> int:
        row1, col1, row2, col2 = row1 + 1, col1 + 1, row2 + 1, col2 + 1
        bottomRight = self.sumMat[row2][col2]
        above = self.sumMat[row1 - 1][col2]
        left = self.sumMat[row2][col1 - 1]
        topLeft = self.sumMat[row1 - 1][col1 - 1]
        return bottomRight - above - left + topLeft
```
