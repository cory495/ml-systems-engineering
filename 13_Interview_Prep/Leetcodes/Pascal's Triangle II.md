```python
class Solution:
    def getRow(self, rowIndex: int) -> List[int]:
        row = [1]

        for i in range(1, rowIndex+1):
            to_add = [1]

            for j in range(1, len(row)):
                to_add.append(row[j] + row[j-1])

            to_add.append(1)
            row = to_add
        
        return row
```

```python
class Solution:
    def getRow(self, rowIndex: int) -> List[int]:
        row = [1]
        for i in range(1, rowIndex + 1):
            row.append(row[-1] * (rowIndex - i + 1) // i)
        return row
```
