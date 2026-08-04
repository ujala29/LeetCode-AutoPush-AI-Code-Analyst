# Max Consecutive Ones III

**Date:** 2026-08-04  
**Difficulty:** 🟡 **Medium**  
**Tags:** `Array` `Binary Search` `Sliding Window` `Prefix Sum`

## Problem Description

Given a binary array nums and an integer k , return the maximum number of consecutive 1 &#39;s in the array if you can flip at most k 0 &#39;s. Example 1: Input: nums = [1,1,1,0,0,0,1,1,1,1,0], k = 2 Output: 6 Explanation: [1,1,1,0,0, 1 ,1,1,1,1, 1 ] Bolded numbers were flipped from 0 to 1. The longest subarray is underlined. Example 2: Input: nums = [0,0,1,1,0,0,1,1,1,0,1,1,0,0,0,1,1,1,1], k = 3 Output: 10 Explanation: [0,0, 1,1, 1 , 1 ,1,1,1, 1 ,1,1 ,0,0,0,1,1,1,1] Bolded numbers were flipped from 0 to 1. The longest subarray is underlined. Constraints: 1 <= nums.length <= 10 5 nums[i] is ei

[LeetCode Link](https://leetcode.com/problems/max-consecutive-ones-iii)

## Approach

Sliding Window

> Maintain a window with at most k zeros to find the maximum consecutive ones

## Solution Logic

1. Initialize two pointers i and j
2. Expand the window to the right and count zeros
3. Shrink the window from the left when zeros exceed k

## Complexity Analysis

| Complexity | Analysis |
|------------|----------|
| **Time:** | O(n) — where n is the length of the input array, as each element is visited at most twice |
| **Space:** | O(1) — as only a constant amount of space is used to store variables |

## Edge Cases Handled

- Empty array
- Array with all zeros
- Array with all ones

## What I Learned

The sliding window technique can be used to efficiently solve problems involving arrays and windows with certain constraints

## Similar Problems

- Max Consecutive Ones
- Subarray with Given Sum

## Solution Code

```text
class Solution:
    def longestOnes(self, nums: List[int], k: int) -> int:

        zeros=0
        i=j=0
        maxcount=0
        while j<len(nums):
            if nums[j]==0:
                zeros+=1
            
            while zeros>k:
                if nums[i]==0:
                    zeros-=1
                
                i+=1
            
            maxcount=max(maxcount,j-i+1)
            j+=1
        return maxcount
```
