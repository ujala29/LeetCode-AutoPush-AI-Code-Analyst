# Remove Element

**Date:** 2026-07-11  
**Difficulty:** 🟢 **Easy**  
**Tags:** `Array` `Two Pointers`

## Problem Description

Given an integer array nums and an integer val , remove all occurrences of val in nums in-place . The order of the elements may be changed. Then return the number of elements in nums which are not equal to val . Consider the number of elements in nums which are not equal to val be k , to get accepted, you need to do the following things: Change the array nums such that the first k elements of nums contain the elements which are not equal to val . The remaining elements of nums are not important as well as the size of nums . Return k . Custom Judge: The judge will test your solution with the fo

[LeetCode Link](https://leetcode.com/problems/remove-element)

## Approach

Two Pointers

> Remove elements from an array in-place using two pointers

## Solution Logic

1. Initialize two pointers at the start and end of the array
2. Compare elements at the pointers and swap if necessary
3. Move pointers based on the comparison result

## Complexity Analysis

| Complexity | Analysis |
|------------|----------|
| **Time:** | O(n) — where n is the number of elements in the array, because we are potentially scanning the entire array once |
| **Space:** | O(1) — because we are modifying the input array in-place and using a constant amount of space |

## Edge Cases Handled

- Empty array
- Array with all elements equal to the target value

## What I Learned

How to efficiently remove elements from an array in-place using two pointers

## Similar Problems

- Remove Duplicates from Sorted Array
- Move Zeroes

## Solution Code

```text
class Solution:
    def removeElement(self, nums: List[int], val: int) -> int:
        # count_val=nums.count(val)
        # n=len(nums)
        # return n-count_val
        n=len(nums)
        i=0
        j=n-1
        while(i<=j):
            if(nums[i]==val):
                if(nums[j]==val):
                    j=j-1
                else:

                    nums[i]=nums[j]
                    i=i+1
                    j=j-1
            else:
               i=i+1

        if(j==-1):
           
            return 0

        return i

```
