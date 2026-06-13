```python
class Solution:

    def mergeArrays(self, nums1: List[List[int]], nums2: List[List[int]]) -> List[List[int]]:

        i, j = 0, 0

        n, m = len(nums1), len(nums2)

  

        res = []

        while i < n and j < m:

            num1 = nums1[i]

            num2 = nums2[j]

  

            if num1[0] < num2[0]:  

                res.append(num1)

                i += 1

            elif num2[0] < num1[0]:

                res.append(num2)

                j += 1

            else:

                val = num1[1] + num2[1]

                res.append([num1[0], val])

                i += 1

                j += 1

        res.extend(nums1[i:n])

        res.extend(nums2[j:m])

        return res
```