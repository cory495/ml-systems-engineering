```python
class Solution:
    def islandPerimeter(self, grid: List[List[int]]) -> int:
        def recursive(row, col):
            if row >= len(grid) or row < 0 or col >= len(grid[0]) or col < 0:
                return 1
            if grid[row][col] == 0:
                return 1
            if grid[row][col] == 1:
                grid[row][col] = -1
                return recursive(row+1, col) + recursive(row-1, col) + recursive(row, col+1) + recursive(row, col-1)
            return 0
        i, j = 0, 0
        while grid[i][j] == 0:
            i += 1
            if i >= len(grid):
                j += 1
                i = 0
        return recursive(i, j)
```

```python
class Solution:
    def islandPerimeter(self, grid: List[List[int]]) -> int:
        m, n, res = len(grid), len(grid[0]), 0
        for i in range(m):
            for j in range(n):
                if grid[i][j] == 1:
                    res += (i + 1 >= m or grid[i + 1][j] == 0)
                    res += (j + 1 >= n or grid[i][j + 1] == 0)
                    res += (i - 1 < 0 or grid[i - 1][j] == 0)
                    res += (j - 1 < 0 or grid[i][j - 1] == 0)
        return res
```

```python
class Solution:
    def islandPerimeter(self, grid: List[List[int]]) -> int:
        m, n = len(grid), len(grid[0])
        res = 0
        for r in range(m):
            for c in range(n):
                if grid[r][c] == 1:
                    res += 4
                    if r and grid[r - 1][c]:
                        res -= 2
                    if c and grid[r][c - 1] == 1:
                        res -= 2
        return res
```
