**Solutions:**

```python
class Solution:

    def removeElement(self, nums: List[int], val: int) -> int:

        i = j = 0

        while i < len(nums):

            while i < len(nums) and nums[i] == val:

                i += 1

            if i >= len(nums):

                break

  

            nums[j] = nums[i]

            i += 1

            j += 1

        return j
```