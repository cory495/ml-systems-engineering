```python
class Solution:
    def buyChoco(self, prices: List[int], money: int) -> int:
        a, b = prices[0], prices[1]

        for price in prices[2:]:
            if a > price or b > price:
                if b >= a:
                    b = price
                else:
                    a = price
        if a + b <= money:
            return money - a - b
        return money
```
