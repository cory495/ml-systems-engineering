```python
class MyHashSet:

    def __init__(self):
        self.arr = []

    def add(self, key: int) -> None:
        self.arr.append(key)

    def remove(self, key: int) -> None:
        for i in reversed(range(len(self.arr))):
            if self.arr[i] == key:
                del self.arr[i]

    def contains(self, key: int) -> bool:
        for i in reversed(range(len(self.arr))):
            if self.arr[i] == key:
                return True
        return False


# Your MyHashSet object will be instantiated and called as such:
# obj = MyHashSet()
# obj.add(key)
# obj.remove(key)
# param_3 = obj.contains(key)
```

```python
class MyHashSet:

    def __init__(self):
        self.data = []

    def add(self, key: int) -> None:
        if key not in self.data:
            self.data.append(key)

    def remove(self, key: int) -> None:
        if key in self.data:
            self.data.remove(key)

    def contains(self, key: int) -> bool:
        return key in self.data


# Your MyHashSet object will be instantiated and called as such:
# obj = MyHashSet()
# obj.add(key)
# obj.remove(key)
# param_3 = obj.contains(key)
```

```python
class MyHashSet:

    def __init__(self):
        self.data = [False] * 1000001

    def add(self, key: int) -> None:
        self.data[key] = True

    def remove(self, key: int) -> None:
        self.data[key] = False

    def contains(self, key: int) -> bool:
        return self.data[key]
```

```python
class MyHashSet:

    def __init__(self):
        # key is in the range [1, 1000000]
        # 31251 * 32 = 1000032
        self.data = 0

    def add(self, key: int) -> None:
        self.data |= (1 << key)

    def remove(self, key: int) -> None:
        self.data &= ~(1 << key)

    def contains(self, key: int) -> bool:
        return bool((self.data >> key) & 1)
```
