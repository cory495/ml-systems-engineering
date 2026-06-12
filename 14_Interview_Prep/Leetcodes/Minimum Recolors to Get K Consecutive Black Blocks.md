```python
class Solution:
    def minimumRecolors(self, blocks: str, k: int) -> int:
        count = 0
        min_change = float('inf')
        
        left = 0
        for right in range(len(blocks)):
            if blocks[right] == 'W':
                count += 1
            if right-left+1 > k:
                if blocks[left] == 'W':
                    count -= 1
                left += 1
            if right-left+1 == k:
                min_change = min(min_change, count)
            right += 1
        return min_change
```
