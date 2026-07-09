```python
class Solution:
    def divideArray(self, nums: List[int]) -> bool:
        seen = set()

        for num in nums:
            if not num in seen:
                seen.add(num)
            else:
                seen.discard(num)
        
        return not seen
```
