```python
class Solution:
    def lemonadeChange(self, bills: List[int]) -> bool:
        dt = {
            5: 0,
            10: 0,
            20: 0
        }

        for bill in bills:
            if bill == 5:
                dt[5] += 1
            elif bill == 10:
                dt[5] -= 1
                dt[10] += 1
            elif bill == 20:
                amount = 20
                if dt[10] > 0:
                    amount -= 10
                    dt[10] -= 1
                while amount > 5:
                    dt[5] -= 1
                    amount -= 5
            if dt[5] < 0 or dt[10] < 0 or dt[20] < 0:
                return False
        return dt[5] >= 0 or dt[10] >= 0 or dt[20] >= 0
```

```python
class Solution:
    def lemonadeChange(self, bills: List[int]) -> bool:
        fives, tens = 0, 0

        for bill in bills:
            if bill == 5:
                fives += 1
            elif bill == 10:
                fives, tens = fives - 1, tens + 1
            elif tens > 0:
                fives, tens = fives - 1, tens - 1
            else:
                fives -= 3
            if fives < 0:
                return False
        return True
```
