# 🔵 LeetCode Tracker

## Stats
- **Total solved:** 0
- **Easy:** 0 | **Medium:** 0 | **Hard:** 0
- **Current streak:** 0 days

---

## Problem Log

| # | Problem | Difficulty | Pattern | Date | Notes |
|---|---------|------------|---------|------|-------|
| 1 | | Easy | | | |

---

## Patterns Learned

### Arrays & Strings
- [ ] Two pointers
- [ ] Sliding window
- [ ] Prefix sum

### Hash Maps & Sets
- [ ] Frequency counting
- [ ] Two Sum pattern

### Binary Search
- [ ] Standard template
- [ ] Search in rotated array

### Stacks & Queues
- [ ] Monotonic stack
- [ ] BFS with deque

### Trees
- [ ] DFS (recursive)
- [ ] BFS (level order)
- [ ] BST properties

### Graphs
- [ ] DFS
- [ ] BFS
- [ ] Union-Find

### Dynamic Programming
- [ ] 1D DP
- [ ] 2D DP

---

## Python Snippets

### Hashmap default
```python
from collections import defaultdict
d = defaultdict(int)
```

### Counter
```python
from collections import Counter
count = Counter(nums)
```

### Deque
```python
from collections import deque
q = deque()
q.append(x)      # add right
q.appendleft(x)  # add left
q.popleft()      # remove left O(1)
```

### Heap (min)
```python
import heapq
heap = []
heapq.heappush(heap, val)
heapq.heappop(heap)
```

### BFS template
```python
from collections import deque
def bfs(root):
    q = deque([root])
    while q:
        node = q.popleft()
        # process node
        for neighbor in node.neighbors:
            q.append(neighbor)
```

### DFS template
```python
def dfs(node, visited):
    if node in visited:
        return
    visited.add(node)
    for neighbor in node.neighbors:
        dfs(neighbor, visited)
```

---

## Problems to Revisit
- 
