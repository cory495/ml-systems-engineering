**Solutions:**

```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        cur_low = float('inf')
        gain = 0
        
        for i in range(len(prices)):
            cur_low = min(cur_low, prices[i])
            if cur_low < prices[i]:
                gain += prices[i] - cur_low
                cur_low = prices[i]
        return gain
```
