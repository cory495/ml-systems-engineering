---
Difficulty: Medium
Topics: Matrix
---

# Word Search

This is a part of [[LeetCode Patterns]].

Given a 2-D grid of characters `board` and a string `word`, return `true` if the word is present in the grid, otherwise return `false`.

For the word to be present it must be possible to form it with a path in the board with horizontally or vertically neighboring cells. The same cell may not be used more than once in a word.

**Example 1:**

![](https://imagedelivery.net/CLfkmk9Wzy8_9HRyug4EVA/7c1fcf82-71c8-4750-3ddd-4ab6a666a500/public)

```java
Input: 
board = [
  ["A","B","C","D"],
  ["S","A","A","T"],
  ["A","C","A","E"]
],
word = "CAT"

Output: true
```

**Example 2:**

![](https://imagedelivery.net/CLfkmk9Wzy8_9HRyug4EVA/79721392-44b6-4de7-c571-d3d1640ac100/public)

```java
Input: 
board = [
  ["A","B","C","D"],
  ["S","A","A","T"],
  ["A","C","A","E"]
],
word = "BAT"

Output: false
```

**Constraints:**

- `1 <= board.length, board[i].length <= 5`
- `1 <= word.length <= 10`
- `board` and `word` consists of only lowercase and uppercase English letters.

**Solutions:**

```python
class Solution:
    def exist(self, board: List[List[str]], word: str) -> bool:
        def backtrace(r, c, on):
            if on == len(word):
                return True
            if r < 0 or r >= len(board) or c < 0 or c >= len(board[0]):
                return False
            if board[r][c] != word[on]:
                return False
            temp = board[r][c]
            board[r][c] = '#'
            found = backtrace(r-1, c, on+1) or \
            backtrace(r+1, c, on+1) or \
            backtrace(r, c-1, on+1) or \
            backtrace(r, c+1, on+1)
            board[r][c] = temp
            return found
        for x in range(len(board)):
            for y in range(len(board[0])):
                if backtrace(x, y, 0):
                    return True
        return False
```
