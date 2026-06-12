```python
class Solution:
    def minWindow(self, s: str, t: str) -> str:
        
        dt = {}
        min_str = ""
        cur_str = ""
        s_len = len(s)
        t_len = len(t)

        for c in t:
            dt[c] = dt.get(c, 0) + 1
        
        left = right = 0

        while right < s_len:
            if s[right] in dt:
                dt[s[right]] -= 1
            
            while all(count <= 0 for count in dt.values()):
                cur_str = s[left:right+1]
                if min_str == "" or len(cur_str) < len(min_str):
                    min_str = cur_str
                
                if s[left] in dt:
                    dt[s[left]] += 1
                left += 1
            
            right += 1
        return min_str
```

```python
class Solution:
    def minWindow(self, s: str, t: str) -> str:
        if not s or not t:
            return ""
        
        dt = {}
        for c in t:
            dt[c] = dt.get(c, 0) + 1
        
        required = len(dt)  # Number of unique characters in t that need to be satisfied
        satisfied = 0       # Number of unique characters currently satisfied
        
        left = right = 0
        min_str = ""
        
        while right < len(s):
            char = s[right]
            
            if char in dt:
                dt[char] -= 1
                # If this character's requirement is now exactly satisfied
                if dt[char] == 0:
                    satisfied += 1
            
            # Try to shrink window while it's valid
            while satisfied == required:
                cur_str = s[left:right+1]
                if min_str == "" or len(cur_str) < len(min_str):
                    min_str = cur_str
                
                left_char = s[left]
                if left_char in dt:
                    dt[left_char] += 1
                    # If removing this character breaks the requirement
                    if dt[left_char] > 0:
                        satisfied -= 1
                left += 1
            
            right += 1
        
        return min_str
```
