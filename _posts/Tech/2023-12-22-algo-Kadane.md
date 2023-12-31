---
layout: post
title: Kadane's Algorithm
categories: Tech-Post Algorithm
description: Kadane's Algorithm
keywords: Algorithm, Data Structure, Kadane's, Leetcode, DSA
---

# Kadane’s algorithm :

## Problem statement 
### 53. Maximum Subarray
Given an integer array nums, find the subarray with the largest sum, and return its sum.

Example 1:
```
Input: nums = [-2,1,-3,4,-1,2,1,-5,4]
Output: 6
Explanation: The subarray [4,-1,2,1] has the largest sum 6.
```

Example 2:
```
Input: nums = [1]
Output: 1
Explanation: The subarray [1] has the largest sum 1.
```

Example 3:
```
Input: nums = [5,4,-1,7,8]
Output: 23
Explanation: The subarray [5,4,-1,7,8] has the largest sum 23.
```

```
Constraints:
1 <= nums.length <= 105
-104 <= nums[i] <= 104

** 
Follow up: 
If you have figured out the O(n) solution.
Try coding another solution using the divide and conquer approach, which is more subtle.
```

#### Solution 

Breaking down problem into to parts: 

1. To Find subarrys And Then find SUM/PRODUCT 

1. First approach was to : 
    1. find subarrays : 
     To Find subarrays we create two for loops : 
     - outer loop will iterate from index i=0 to n (nums.length).
     - inner loop will iterate from j=i+1 to n.
     Then we will create a list to append these subarrays
        
        ```python
        Sub_arr=[]
        for i in range(0, len(nums):
        	for j in range(i, len(nums):
        			val = nums[i:J]
        			sub_arr.append(val)
        			j+=1
        
        ```
        Let's break down the given code and analyze its time and space complexity:
        This code generates all possible subarrays of the input array nums and appends them to the sub_arr list. Let's analyze the time and space complexity:

        Time Complexity:

        The outer loop runs len(nums) times, where n is the length of the input array.
        The inner loop runs from i to len(nums), where i varies from 0 to len(nums) - 1.
        For each combination of i and j, a subarray is extracted using slicing (nums[i:j]), and it takes O(j - i) time.
        The total time complexity is the sum of the time taken for each subarray, resulting in a time complexity of O(1 + 2 + 3 + ... + n), which is O(n^2/2) or simply O(n^2) in big O notation.
        
        Space Complexity:

        The sub_arr list stores all the generated subarrays.
        The number of subarrays is the sum of the series 1 + 2 + 3 + ... + n, which is O(n^2/2) or simply O(n^2).
        Therefore, the space complexity is O(n^2).
        In summary:

        Time Complexity: O(n^2)
        Space Complexity: O(n^2)
        This code can be optimized to achieve a better time complexity, but the current implementation provides a straightforward way to understand the generation of all subarrays.
        
    2. Optimised solution to find subarays : 
    
    ```python
    i=0
    while (i<len(nums)):
    	while (j<len(nums)):
    		j=i
    		val=nums[i:i+1]
    		sub_arr.append(val)
    		j+=1
    	i+=1
    ```
    
    now find sum of subarray : 
    
    1. FIRST naive approach : 
    
    ```python
    		sum_sub_array=[]
    		for m in range(len(sub_arr)):
    		sub_array = sub_arr[m]
    		
    			for n in range(len(sub_array)):
    		
    				if len(sub_array)>1:
    		
    					sum_sub=sum_sub[n]+sum_sub[n+1]
    		
    					sum_sub_array.append(sum_sub)
    		l=len(sum_sub_array)
    		print(sum_sub_array[l-1])
    ```
    
    1. A better approach : 

```python
for sub_arr in arr: 
	sum_sub=sum(sub_arr)
	sum_sub_arr.append(sum_sub)
	print(max(sum_sub_arr))

```

STILL we can use a better approach (kadane’s) to solve this:

```python
curSum=0
maxSum=-1e8 #-1e8 is lowest negative number 
for i in range(0, len(nums)):
	curSum = curSum+nums[i]
	if curSum > maxSum:
		maxSum = curSum
	if curSum < 0:
		curSum = 0 
return maxSum

**#time complexity is 0(n)
#space complexity is 0(1)**
```

## Kadane’s product problem : 
### 152. Maximum Product Subarray

Given an integer array nums, find a subarray that has the largest product, and return the product.

```
Example 1:
Input: nums = [2,3,-2,4]
Output: 6
Explanation: [2,3] has the largest product 6.
```
```
Example 2:
Input: nums = [-2,0,-1]
Output: 0
Explanation: The result cannot be 2, because [-2,-1] is not a subarray.
```

```
Constraints:

1 <= nums.length <= 2 * 104
-10 <= nums[i] <= 10
```

```python
class Solution:
def maxProduct(self, nums: List[int]) -> int:
	maximumProduct = 1
	minProduct = 1
	result = -1e8
	for num in nums:
		if num < 0:
			maximumProduct, minProduct = minProduct, maximumProduct
		maximumProduct = max(num, maximumProduct * num)
		minProduct = min(num, minProduct * num)
		result = max(result, maximumProduct)
	return result
```