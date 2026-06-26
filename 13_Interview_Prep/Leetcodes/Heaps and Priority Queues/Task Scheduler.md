---
Difficulty: Medium
Topics: Heaps
Created: 2026-06-01
Updated: 2026-06-26
tags:
  - interview
  - programming
Type: Interview
---
# Task Scheduler

This is a part of [[LeetCode Patterns]].

You are given an array of CPU tasks `tasks`, where `tasks[i]` is an uppercase english character from `A` to `Z`. You are also given an integer `n`.

Each CPU cycle allows the completion of a single task, and tasks may be completed in any order.

The only constraint is that **identical** tasks must be separated by at least `n` CPU cycles, to cooldown the CPU.

Return the _minimum number_ of CPU cycles required to complete all tasks.

**Example 1:**

```java
Input: tasks = ["X","X","Y","Y"], n = 2

Output: 5
```

Explanation: A possible sequence is: X -> Y -> idle -> X -> Y.

**Example 2:**

```java
Input: tasks = ["A","A","A","B","C"], n = 3

Output: 9
```

Explanation: A possible sequence is: A -> B -> C -> Idle -> A -> Idle -> Idle -> Idle -> A.

**Constraints:**

- `1 <= tasks.length <= 1000`
- `0 <= n <= 100`

**Solutions:**

```python
class Solution:

    def leastInterval(self, tasks: List[str], n: int) -> int:

        count = Counter(tasks)

        maxHeap = [-cnt for cnt in count.values()]

        heapq.heapify(maxHeap)

  

        time = 0

        q = deque()  # pairs of [-cnt, idleTime]

        while maxHeap or q:

            time += 1

  

            if not maxHeap:

                time = q[0][1]

            else:

                cnt = 1 + heapq.heappop(maxHeap)

                if cnt:

                    q.append([cnt, time + n])

            if q and q[0][1] == time:

                heapq.heappush(maxHeap, q.popleft()[0])

        return time
```