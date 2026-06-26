---
Created: 2026-06-01
Updated: 2026-06-26
tags:
  - interview
  - programming
Type: Interview
---
```python
class Solution:
    def rotate(self, matrix: List[List[int]]) -> None:
        n = len(matrix)

        matrix[:] = [[matrix[j][i] for j in range(n)] for i in range(n)]
        matrix[:] = [row[::-1] for row in matrix]
```
