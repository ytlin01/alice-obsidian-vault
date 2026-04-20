---
title: Arrays and Strings
created: 2026-04-20
tags: [concept, knowledge, ds-interview, leetcode]
topics: [arrays, strings, two-pointers, sliding-window]
---

# Arrays and Strings

> Arrays and strings are the foundation for indexing, traversal, and many of the most common interview patterns.

---

## What It Is

### Arrays
- An array stores items in **order**, which makes index-based access fast and predictable. 
- An array can't be resized; a list (dynamic array) can.
- In Python, we don't have to worry about the type of data we store in the list or the size of the list

### Strings
- In Python, strings are **immutable**
	- **Mutable**: a type of data that can be changed
	- **Immutable**: a type of data that cannot be changed.

![[Pasted image 20260420182429.png]]


---

## Why It Matters
This is usually the first place where interview pattern recognition starts to click. A lot of problems that look different on the surface reduce to a few repeatable moves:
- scan left to right
- compare two positions
- maintain a running window
- precompute information like counts or prefix sums
- update in place when space matters

Getting comfortable here makes later topics like hash maps, stacks, and dynamic programming easier to learn.

---

## Techniques
- Use `two pointers` when you need to compare values from two ends or compact an array in place.
- Use a `sliding window` when the problem asks about a best or valid contiguous substring/subarray.
- Use `prefix sums` when repeated range calculations would otherwise be too slow.

---

## Two Pointers
- two **integer variables** that both move along an **iterable**
- **Reverse String**: start the pointers at the edges of the input. Move them towards each other until they meet.
	- O(n) iterations in while loop
	- If each iteration is O(1), the runtime will be linear

- Pseudocode:
```
function fn(arr):
    left = 0
    right = arr.length - 1

    while left < right:
        Do some logic here depending on the problem
        Do some more logic here to decide on one of the following:
            1. left++
            2. right--
            3. Both left++ and right--
```


---

## Key Question Types
- Two sums

---

## Connected To
- [[LeetCode Data Structures Course]] - this is the first concept in the course
- [[LeetCode Patterns]] - arrays and strings patterns live in the main pattern checklist
- [[LeetCode Tracker]] - problems solved in this area should be logged there

---

## Where I Learned This
- [[LeetCode Data Structures Course]] *(course)*
