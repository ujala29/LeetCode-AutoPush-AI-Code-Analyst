# Squares of a Sorted Array

**Date:** 2026-07-18  
**Difficulty:** 🟢 **Easy**  
**Tags:** `Array` `Two Pointers` `Sorting`

## Problem Description

Given an integer array nums sorted in non-decreasing order, return an array of the squares of each number sorted in non-decreasing order . Example 1: Input: nums = [-4,-1,0,3,10] Output: [0,1,9,16,100] Explanation: After squaring, the array becomes [16,1,0,9,100]. After sorting, it becomes [0,1,9,16,100]. Example 2: Input: nums = [-7,-3,2,3,11] Output: [4,9,9,49,121] Constraints: 1 <= nums.length <= 10 4 -10 4 <= nums[i] <= 10 4 nums is sorted in non-decreasing order. Follow up: Squaring each element and sorting the new array is very trivial, could you find an O(n) solution using a different a

[LeetCode Link](https://leetcode.com/problems/squares-of-a-sorted-array)

## Approach

Two Pointers

> Sort squares of numbers in non-decreasing order using two pointers

## Solution Logic

1. Find the first non-negative number
2. Initialize two pointers, one before and one after the non-negative number
3. Compare the absolute values of the numbers at the two pointers and add the smaller one to the result

## Complexity Analysis

| Complexity | Analysis |
|------------|----------|
| **Time:** | O(n) — where n is the number of elements in the input array, because we are scanning the array once |
| **Space:** | O(n) — where n is the number of elements in the input array, because we are storing the result in a new array |

## Edge Cases Handled

- All negative numbers
- All non-negative numbers
- Mix of negative and non-negative numbers

## What I Learned

Using two pointers can be an efficient way to solve problems that involve comparing and sorting elements in an array

## Similar Problems

- Merge Sorted Arrays
- Squares of a Sorted Array

## Solution Code

```text
class Solution:
    def sortedSquares(self, nums: List[int]) -> List[int]:
        pos=0
        position=-1
        for i in range(0,len(nums)):
            if nums[i]>=0:
                pos=nums[i]
                position=i
                break
        ans=[]
        
        if position==-1:
            i=len(nums)-1
            while i>=0:
               ans.append(nums[i]*nums[i])
               i-=1
        elif position==0:
            for i in range(0,len(nums)):
                ans.append(nums[i]*nums[i])
        
        else:
            i=position-1
            j=position+1
            if abs(nums[i])<pos:
                position=i
                i=position-1
                pos=nums[position]
                j=position+1
            ans.append(pos*pos)
            while i>=0 and j<len(nums):
                distfromleft=abs(pos-abs(nums[i]))
                distfromright=abs(pos-nums[j])
                if distfromleft<distfromright:
                    ans.append(nums[i]*nums[i])
                    i-=1
                else:
                    ans.append(nums[j]*nums[j])
                    j+=1
            
            while i>=0:
                ans.append(nums[i]*nums[i])
                i-=1
            while j<len(nums):
                ans.append(nums[j]*nums[j])
                j+=1
        
        return ans



```
