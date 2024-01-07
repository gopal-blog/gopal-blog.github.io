---
layout: post
title: Binary Search Algorithm
categories: Tech-Post Algorithm
description: Binary Search Algorithm
keywords: Algorithm, Data Structure, Binary Search, Leetcode, DSA
---
Best template for Binary Search : 

```python
def binarySearch():
    s = 0               ### a start index (a valid index)
    e = len(something)  ### the total length of something (an invalid index, assuming 0-indexed)
    while s+1<e:
        mid = (s+e)//2
        ### when we check mid, if it meets the condition, we assign mid to s
        ### because we want to make sure s is always at a valid index
        if check(mid):
            s = mid
        else:
            e = mid
    return s
```

Easiest demonstration : 

```python
arr=[9,3,2,5,8]
    
key=5
start=0
end=len(arr)-1

while start<=end:
    mid = start+end//2
    if arr[mid] == key:
        print(mid) 
    elif key>mid:
        start=mid+1
    else:
        end=mid-1
    print(mid)
```

Space Complexity:

- The space complexity is determined by the size of the input array. In this case, it is O(1) as there are no additional data structures used that scale with the input size.

Time Complexity:

- Binary search is a divide-and-conquer algorithm that continuously halves the search space.
- The time complexity of binary search is O(log n), where n is the number of elements in the array.
- In each iteration of the while loop, the search space is halved, resulting in a logarithmic time complexity.
- The print statements within the loop do not affect the overall time complexity.

In summary, the space complexity is O(1), and the time complexity is O(log n) for the binary search algorithm. It is an efficient search algorithm for sorted arrays, allowing for faster searching compared to linear search.
