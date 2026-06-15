```python
class TimeMap:

    def __init__(self):
        self.timestamps = {}

    def set(self, key: str, value: str, timestamp: int) -> None:
        self.timestamps[key] = self.timestamps.get(key, []) + [[timestamp, value]]

    def get(self, key: str, timestamp: int) -> str:
        arr = self.timestamps.get(key, [])

        n = len(arr)
        l, r = 0, n-1
        res = ""

        while l <= r:
            mid = (l+r)//2

            if arr[mid][0] <= timestamp:
                res = arr[mid][1]
                l = mid + 1
            else:
                r = mid - 1
        return res
```
