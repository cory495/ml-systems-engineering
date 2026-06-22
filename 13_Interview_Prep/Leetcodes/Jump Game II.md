```python
class Solution:
    def jump(self, nums: List[int]) -> int:
        cur_idx = 0
        jump_count = 0
        cur_best_next = 0

        for i in range(1, len(nums)):
            if cur_best_next == cur_idx or nums[i] + i > nums[cur_best_next] + cur_best_next:
                cur_best_next = i
            if i >= nums[cur_idx] + cur_idx or i == len(nums)-1:
                cur_idx = cur_best_next
                jump_count += 1
        return jump_count
```
