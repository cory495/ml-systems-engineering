**Solutions:**

```python
class Solution:
    def majorityElement(self, nums: List[int]) -> List[int]:
        goal_count = len(nums) //  3
        dt = {}

        for i in nums:
            dt[i] = dt.get(i, 0) + 1
        
        res = []
        for key, val in dt.items():
            if val > goal_count:
                res.append(key)
        return res
```

```python
class Solution:
    def majorityElement(self, nums: List[int]) -> List[int]:
        goal_count = len(nums) //  3
        dt = {}
        res = []

        for num in nums:
            dt[num] = dt.get(num, 0) + 1
            if dt[num] == goal_count + 1:
                res.append(num)
            if len(res) == 2:
                break
        return res
```
