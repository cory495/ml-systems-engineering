```python
class Solution:
    def sortArray(self, nums: List[int]) -> List[int]:
        def merge_sort(nums):
            n = len(nums)
            if n < 2:
                return nums
            mid = n // 2
            return merge(merge_sort(nums[:mid]), merge_sort(nums[mid:]))

        def merge(nums1, nums2):
            i, j = 0, 0
            n, m = len(nums1), len(nums2)
            ans = []

            while i < n and j < m:
                if nums1[i] < nums2[j]:
                    ans = ans + [nums1[i]]
                    i += 1
                else:
                    ans = ans + [nums2[j]]
                    j += 1
            if i < n:
                ans = ans + nums1[i:]
            if j < m:
                ans = ans + nums2[j:]
            return ans
        
        return merge_sort(nums)
```
