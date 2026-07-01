```python
class Solution:
    def combinationSum4(self, nums: List[int], target: int) -> int:
        res = []
        def dfs(cur, s=0):
            if s == target:
                res.append(cur)
                return
            if s > target:
                return
            for num in nums:
                s += num
                cur.append(num)
                dfs(cur, s)

                s -= num
                cur.pop()
        
        dfs([])
        return len(res)
```

```python
class Solution:
    def combinationSum4(self, nums: List[int], target: int) -> int:
        nums.sort()

        def dfs(total):
            if total == 0:
                return 1

            res = 0
            for i in range(len(nums)):
                if total < nums[i]:
                    break
                res += dfs(total - nums[i])
            return res

        return dfs(target)
```

```python
class Solution:
    def combinationSum4(self, nums: List[int], target: int) -> int:
        nums.sort()
        dp = defaultdict(int)
        dp[target] = 1
        for total in range(target, 0, -1):
            for num in nums:
                if total < num:
                    break
                dp[total - num] += dp[total]
        return dp[0]
```
