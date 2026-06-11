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
```python
```python
class Solution:
    def sortArray(self, nums: List[int]) -> List[int]:
        def merge_sort(nums):
            if len(nums) <= 1:
                return nums
            
            mid = len(nums) // 2
            left = merge_sort(nums[:mid])
            right = merge_sort(nums[mid:])
            return merge(left, right)

        def merge(nums1, nums2):
            i = j = 0
            result = []
            
            while i < len(nums1) and j < len(nums2):
                if nums1[i] <= nums2[j]:
                    result.append(nums1[i])
                    i += 1
                else:
                    result.append(nums2[j])
                    j += 1
            
            result.extend(nums1[i:])
            result.extend(nums2[j:])
            return result
        
        return merge_sort(nums)
```
