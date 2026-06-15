---
Difficulty: Medium
Topics: Arrays
---
# Valid Sudoku

This is a part of [[LeetCode Patterns]].

You are given a `9 x 9` Sudoku board `board`. A Sudoku board is valid if the following rules are followed:

1. Each row must contain the digits `1-9` without duplicates.
2. Each column must contain the digits `1-9` without duplicates.
3. Each of the nine `3 x 3` sub-boxes of the grid must contain the digits `1-9` without duplicates.

Return `true` if the Sudoku board is valid, otherwise return `false`

Note: A board does not need to be full or be solvable to be valid.

**Example 1:**

![](https://imagedelivery.net/CLfkmk9Wzy8_9HRyug4EVA/0be40c5d-2d18-42b8-261b-13ca50de4100/public)

```java
Input: board =
[["1","2",".",".","3",".",".",".","."],
 ["4",".",".","5",".",".",".",".","."],
 [".","9","8",".",".",".",".",".","3"],
 ["5",".",".",".","6",".",".",".","4"],
 [".",".",".","8",".","3",".",".","5"],
 ["7",".",".",".","2",".",".",".","6"],
 [".",".",".",".",".",".","2",".","."],
 [".",".",".","4","1","9",".",".","8"],
 [".",".",".",".","8",".",".","7","9"]]

Output: true
```

**Example 2:**

```java
Input: board =
[["1","2",".",".","3",".",".",".","."],
 ["4",".",".","5",".",".",".",".","."],
 [".","9","1",".",".",".",".",".","3"],
 ["5",".",".",".","6",".",".",".","4"],
 [".",".",".","8",".","3",".",".","5"],
 ["7",".",".",".","2",".",".",".","6"],
 [".",".",".",".",".",".","2",".","."],
 [".",".",".","4","1","9",".",".","8"],
 [".",".",".",".","8",".",".","7","9"]]

Output: false
```

Explanation: There are two 1's in the top-left 3x3 sub-box.

**Constraints:**

- `board.length == 9`
- `board[i].length == 9`
- `board[i][j]` is a digit `1-9` or `'.'`.

**Solutions:**
```python
class Solution:

    def isValidSudoku(self, board: List[List[str]]) -> bool:

        def checkBox(board, x, y):

            vals = set()

            for i in range(3):

                for j in range(3):

                    num = board[x+i][y+j]

                    if num.isdigit() and num in vals:

                        return False

                    vals.add(num)

            return True

        def checkColumn(board, x):

            vals = set()

            for i in range(9):

                num = board[i][x]

                if num.isdigit() and num in vals:

                    return False

                vals.add(num)

            return True

        def checkRow(arr):

            vals = set()

            for num in arr:

                if num.isdigit() and num in vals:

                    return False

                vals.add(num)

            return True

        for i in range(len(board)):

            if not checkRow(board[i]):

                return False

            if not checkColumn(board, i):

                return False

        for i in range(3):

            for j in range(3):

                if not checkBox(board, i*3, j*3):

                    return False

        return True
```

The above approach was using the naive approach. The next thought was how can I only visit each value once. The idea, then, came to create the sets and add to look at the sets based on the row, column, and box. This means each box is visited only once. This is `O(81)` instead of `O(9*9*3)`. While both technically simplify to `O(1)`, it is easy to see that the bottom solution is more efficient.
```python
class Solution:

    def isValidSudoku(self, board: List[List[str]]) -> bool:

        rows = [set() for _ in range(9)]

        cols = [set() for _ in range(9)]

        boxes = [set() for _ in range(9)]

  

        for r in range(9):

            for c in range(9):

                val = board[r][c]

                if val == ".":

                    continue

                b = (r // 3) * 3 + (c // 3)

  

                if val in rows[r] or val in cols[c] or val in boxes[b]:

                    return False

                rows[r].add(val)

                cols[c].add(val)

                boxes[b].add(val)

        return True
```