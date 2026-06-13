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