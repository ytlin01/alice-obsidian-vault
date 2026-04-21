---
title: LeetCode Patterns
created: 2026-04-17
tags: [knowledge, ds-interview, leetcode, algorithms]
topics: [algorithms, data-structures]
---

# LeetCode Patterns

> Quick-reference note for pattern recognition. Use [[LeetCode Tracker]] for problem logs and weak spots.

---

## How To Use This Note

1. Identify the input shape: array, string, tree, graph, matrix.
2. Look for the signal: sorted, contiguous, repeated, shortest path, parent-child, overlap.
3. Match it to one pattern family below.
4. If stuck, write the simplest brute force first, then ask what repeated work can be removed.

---

## Pattern Map

### Arrays & Strings

| Pattern | Reach for it when... | Common move |
|---|---|---|
| Two pointers | array/string is sorted, or you compare from both ends | move `l` / `r` based on condition |
| Sliding window | need longest/shortest/number of valid contiguous subarrays | expand right, shrink left |
| Prefix sum | repeated range-sum checks | precompute running totals |
| Hash map / set | need fast lookup, counts, duplicates, complement search | store seen values or frequencies |

### Search

| Pattern | Reach for it when... | Common move |
|---|---|---|
| Binary search | sorted search space or "minimum valid answer" | cut search space in half |
| Binary search on answer | asking for smallest/largest feasible value | test feasibility with helper |

### Stack / Queue

| Pattern | Reach for it when... | Common move |
|---|---|---|
| Monotonic stack | next greater/smaller element, histogram, span | pop until stack order works |
| Queue / BFS | level-by-level exploration or shortest path in unweighted graph | `popleft()` and push neighbors |

### Trees & Graphs

| Pattern | Reach for it when... | Common move |
|---|---|---|
| DFS | need full traversal, recursion, path building | recurse on children / neighbors |
| BFS | need minimum steps or level order | queue frontier nodes |
| Union-Find | need connected components with many merge/check operations | union roots, path compress |

### Dynamic Programming

| Pattern | Reach for it when... | Common move |
|---|---|---|
| 1D DP | answer depends on earlier positions or smaller totals | define `dp[i]` clearly |
| 2D DP | state depends on two positions or two strings | build table by row/column |

---

## Recognition Cues

- `sorted` -> two pointers or binary search
- `subarray / substring` -> sliding window or prefix sum
- `top k / smallest / largest` -> heap
- `tree path / depth / ancestor` -> DFS
- `minimum steps` -> BFS
- `same work repeated` -> DP
- `groups / connectivity` -> graph traversal or Union-Find

---

## Python Quick Reference

### Counting
```python
from collections import defaultdict
count = defaultdict(int)
```

### Frequency shortcut
```python
from collections import Counter
count = Counter(nums)
```

### Queue
```python
from collections import deque
q = deque()
q.append(x)
q.popleft()
```

### Min-heap
```python
import heapq
heap = []
heapq.heappush(heap, val)
heapq.heappop(heap)
```

### BFS
```python
from collections import deque
def bfs(start):
    q = deque([start])
    seen = {start}
    while q:
        node = q.popleft()
        # process node
        for neighbor in node.neighbors:
            if neighbor not in seen:
                seen.add(neighbor)
                q.append(neighbor)
```

### DFS
```python
def dfs(node, visited):
    if node in visited:
        return
    visited.add(node)
    for neighbor in node.neighbors:
        dfs(neighbor, visited)
```

### Binary search
```python
def binary_search(nums, target):
    l, r = 0, len(nums) - 1
    while l <= r:
        m = (l + r) // 2
        if nums[m] == target:
            return m
        if nums[m] < target:
            l = m + 1
        else:
            r = m - 1
    return -1
```

---

## Connected To
- [[Dashboard]]
- [[LeetCode Tracker]]
- [[SQL Patterns]]
- [[ML Concepts]]
- [[Resources]]
