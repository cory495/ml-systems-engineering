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
