---
layout: post
title: Leetcode 169
categories: Tech-Post Leetcode
description: Leetcode Solution in python
keywords: Algorithm, Data Structure, Leetcode, DSA, Python
---

# 169. Majority Element

## Problem Statement :

Given an array nums of size n, return the majority element.

The majority element is the element that appears more than ⌊n / 2⌋ times. You may assume that the majority element always exists in the array.

## Example : 

### Example 1:
```
Input: nums = [3,2,3]
Output: 3
```

### Example 2:
```
Input: nums = [2,2,1,1,1,2,2]
Output: 2
```

## Constraints:
```
n == nums.length
1 <= n <= 5 * 104
-109 <= nums[i] <= 109
```

## Solution (Py3) : 
```python
  class Solution:
    def majorityElement(self, nums: List[int]) -> int:
        nums.sort()
        return nums[len(nums)//2]
```
