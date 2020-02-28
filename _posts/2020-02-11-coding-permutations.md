---
layout: post
title:  "Competitive coding: Permutation generating using recursive function"
date:   2020-02-11 22:21:00 +0900
categories: recursion competitive-coding permutation
---

# Competitive coding from Leetcode

Problem statement number `#46` <https://leetcode.com/problems/permutations/>. It is a medium level problem and following is a given problem statement.

Problem: Given a collection of distinct integers, return all possible permutations.

Sample input and output:

```
Input: [1,2,3]
Output:
[
  [1,2,3],
  [1,3,2],
  [2,1,3],
  [2,3,1],
  [3,1,2],
  [3,2,1]
]
```

## Solution

Since its permutation type of problem and the output must be all possible permutations, then we can achieve this by applying `Heap's Algorithm`, <https://en.wikipedia.org/wiki/Heap%27s_algorithm>. 

Heap's algorithm generate permutations by swapping two elements from the given array. I will explain more detail in following example.

## Example

Let's say we have an array [2,1,3], by using Heap's algorithm we can generate permutation like below.

1. First of all arr size is 3, so it will start from `i=0` to `i<=len(arr)-1`. 
2. Iterate through number of elements and check.
3. Swap two elements based on their even or odd. 
4. If element is even, swap the ith elem to last elem.
5. If element is odd, swap first and last elem.
   
## Sample code


```py
class Solution:
    def permute(self, nums: List[int]) -> List[List[int]]:
        n = len(nums)
        res = []
        self.heapAlgorithm(n, nums, res)
        return res
    def heapAlgorithm(self, k, nums, res):
        if k==1:
            # copy of the all array
            res.append(nums[:])
        else:
            self.heapAlgorithm(k-1, nums, res)
            for i in range (0, k-1):
                # swap
                # k&1 means odd elem
                if k&1:
                    # swap first and last elem
                    nums[0], nums[k-1] = nums[k-1],nums[0] 
                else:
                    # swap ith and last elem
                    nums[i], nums[k-1] = nums[k-1],nums[i] 
                self.heapAlgorithm(k-1, nums, res)
```

This algo runtime is 32ms and memory usage is 12.9mb.