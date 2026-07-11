# Remove Duplicates from Sorted Array

**Date:** 2026-07-11  
**Difficulty:** 🟢 **Easy**  
**Tags:** `Array` `Two Pointers`

## Problem Description

Given an integer array nums sorted in non-decreasing order , remove the duplicates in-place such that each unique element appears only once . The relative order of the elements should be kept the same . Consider the number of unique elements in nums to be k ​​​​​​​ ​​​​​​​. After removing duplicates, return the number of unique elements k . The first k elements of nums should contain the unique numbers in sorted order . The remaining elements beyond index k - 1 can be ignored. Custom Judge: The judge will test your solution with the following code: int[] nums = [...]; // Input array int[] expe

[LeetCode Link](https://leetcode.com/problems/remove-duplicates-from-sorted-array)

## Approach

Two Pointers

> Use two pointers to track unique elements in a sorted array

## Solution Logic

1. Initialize two pointers, i and j, to the start of the array
2. Compare elements at i and j, if different, move i forward and copy the element at j to i
3. Repeat the comparison and copying process until j reaches the end of the array

## Complexity Analysis

| Complexity | Analysis |
|------------|----------|
| **Time:** | O(n) — where n is the number of elements in the array, because we are scanning the array once |
| **Space:** | O(1) — because we are modifying the input array in-place and using a constant amount of space |

## Edge Cases Handled

- Array with one element
- Array with all duplicate elements

## What I Learned

How to efficiently remove duplicates from a sorted array while preserving the relative order of elements

## Similar Problems

- Remove Duplicates from Unsorted Array
- Find First Duplicate in Array

## Solution Code

```text
class Solution:
    def removeDuplicates(self, nums: List[int]) -> int:
        n=len(nums)
        i=0
        j=1
        if(n==1):
           return 1
        while(j<n):
            if(nums[i]!=nums[j]):
                i=i+1
                nums[i]=nums[j]
                
            j=j+1
        return i+1           

        
```
