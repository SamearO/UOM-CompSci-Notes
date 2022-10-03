# Two Panels example problem

## Problem Statement
Given a list of integers `a` and an integer `k`, are there 2 integers in `a` that multiply to get `k`?

## Naive Solution
This solution essentially loops over the array for every element in the array. Hence its complexity is `O(n^2)`

```python
def search(a, k):
    for i in range(len(a)):
        for j in range(i+1, len(a)):
            if a[i]*a[j] == k:
                return True
    return False
```

## Sort and Two Pointer Solution

The array is sorted so increasing `i` leads to a higher numbers and decreasing `j` leads to a lower number. Hence the loop itself is in `O(n)` however, sorting is done in `O(nlogn)`. Since `O(nlogn)` is larger, the time complexity of this solution is `O(nlogn)`

```python
def search(a, k):
    i = 0
    j = len(a) - 1
    a.sort()

    while i<j:
        if a[i]*a[j] == k:
            return True
        elif a[i]*a[j] < k:
            i += 1
        else:
            j -= 1
    return False
```

## Remembering solution
Since finding if an element in a `hashset` is an `O(1)` operation, this solution is `O(n)`.

```python
def search(a, k):
    found = set()
    for i in range(len(a)):
        if k/a[i] in found:
            return True
        else:
            found.add(a[i])
    return False
```