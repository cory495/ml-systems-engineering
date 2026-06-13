**Solutions:**

```python
class Solution:

    def applyOperations(self, nums: List[int]) -> List[int]:

        n = len(nums)

        for i in range(n-1):

            if nums[i] == nums[i+1]:

                nums[i] *= 2

                nums[i+1] = 0

        i = j = count = 0

        while i < n and j < n:

            while i<n-1 and nums[i] == 0:

                i += 1

                count += 1

            nums[j] = nums[i]

            i += 1

            j += 1

        for j in range(n-count, n):

            nums[j] = 0

        return nums
```

```python
class Solution:

    def applyOperations(self, nums: List[int]) -> List[int]:

        n = len(nums)

  

        for i in range(n - 1):

            if nums[i] == nums[i + 1]:

                nums[i] *= 2

                nums[i + 1] = 0

  

        j = 0

        for i in range(n):

            if nums[i]:

                nums[j] = nums[i]

                j += 1

  

        while j < n:

            nums[j] = 0

            j += 1

  

        return nums
```