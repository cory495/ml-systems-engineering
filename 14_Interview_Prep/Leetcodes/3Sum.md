```python
class Solution:
    def threeSum(self, nums: List[int]) -> List[List[int]]:
        solutions = set()
        for i in range(len(nums)):
            for j in range(i+1, len(nums)):
                for k in range(j+1, len(nums)):
                    if nums[i]+nums[j]+nums[k]==0:
                        solutions.add(tuple(sorted([nums[i], nums[j], nums[k]])))
        return list(solutions)
```

```python
class Solution:
    def threeSum(self, nums: List[int]) -> List[List[int]]:
        n = len(nums)
        nums = sorted(nums)
        solutions = []
        
        for i in range(n - 2):
            if i > 0 and nums[i] == nums[i - 1]:
                continue
            
            left, right = i + 1, len(nums) - 1

            while left < right:
                sum_val = nums[left] + nums[i] + nums[right]
                if sum_val < 0:
                    left += 1
                elif sum_val > 0:
                    right -= 1
                else:
                    solutions.append([nums[left], nums[i], nums[right]])
                    while left < right and nums[left] == nums[left + 1]:
                        left += 1
                    while left < right and nums[right] == nums[right - 1]:
                        right -= 1
                    left += 1
                    right -= 1

        return solutions
```
