```python
class Solution:
    def merge(self, nums1: List[int], m: int, nums2: List[int], n: int) -> None:
        """
        Do not return anything, modify nums1 in-place instead.
        """
        i = j = 0
        res = []
        while i < m and j < n:
            if nums1[i] < nums2[j]:
                res.append(nums1[i])
                i+= 1
            else:
                res.append(nums2[j])
                j += 1
        res.extend(nums1[i:m])
        res.extend(nums2[j:n])
        
        while res[-1] == 0:
            res.pop()

        nums1[:] = res[:]
```
