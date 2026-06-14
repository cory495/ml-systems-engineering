
**Solutions:**
```python
class Solution:

    def rob(self, nums: List[int]) -> int:

        rob1, rob2 = 0, 0

  

        if len(nums) == 0:

            return 0

  

        if len(nums) == 1:

            return nums[0]

  

        for num in nums[:-1]:

            rob1, rob2 = rob2, max(num + rob1, rob2)

  

        rob3, rob4 = 0, 0

        for num in nums[1:]:

            rob3, rob4 = rob4, max(num + rob3, rob4)

        return max(rob2, rob4)
```

```python
class Solution:

    def rob(self, nums: List[int]) -> int:

  

        if len(nums) == 1:

            return nums[0]

        def rob_line(arr):

            prev = curr = 0

            for x in arr:

                prev, curr = curr, max(curr, prev + x)

            return curr

  

        return max(rob_line(nums[1:]), rob_line(nums[:-1]))
```