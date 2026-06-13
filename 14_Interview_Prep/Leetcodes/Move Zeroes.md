```python
class Solution:

    def moveZeroes(self, nums: List[int]) -> None:

        """

        Do not return anything, modify nums in-place instead.

        """

        i = j = 0

        n = len(nums)

  

        while i < n and j < n:

            while j < n and nums[j] == 0:

                j += 1

            if j >= n:

                break

            nums[i] = nums[j]

            i += 1

            j += 1

        while i < n:

            nums[i] = 0

            i += 1
```

```python
class Solution:

    def moveZeroes(self, nums: List[int]) -> None:

        i = 0

  

        for j in range(len(nums)):

            if nums[j] != 0:

                nums[i] = nums[j]

                i += 1

  

        while i < len(nums):

            nums[i] = 0

            i += 1
```