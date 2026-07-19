# Duplicate Zeros

**Date:** 2026-07-19  
**Difficulty:** 🟢 **Easy**  
**Tags:** `Array` `Two Pointers`

## Problem Description

Given a fixed-length integer array arr , duplicate each occurrence of zero, shifting the remaining elements to the right. Note that elements beyond the length of the original array are not written. Do the above modifications to the input array in place and do not return anything. Example 1: Input: arr = [1,0,2,3,0,4,5,0] Output: [1,0,0,2,3,0,0,4] Explanation: After calling your function, the input array is modified to: [1,0,0,2,3,0,0,4] Example 2: Input: arr = [1,2,3] Output: [1,2,3] Explanation: After calling your function, the input array is modified to: [1,2,3] Constraints: 1 <= arr.length 

[LeetCode Link](https://leetcode.com/problems/duplicate-zeros)

## Approach

Two Pointers

> Duplicate zeros in array by shifting elements to the right

## Solution Logic

1. Count zeros in the array
2. Initialize two pointers at the end of the array
3. Copy elements from the left pointer to the right pointer, handling zeros by inserting an extra zero

## Complexity Analysis

| Complexity | Analysis |
|------------|----------|
| **Time:** | O(n) — where n is the number of elements in the array, as we only traverse the array once |
| **Space:** | O(1) — as we only use a constant amount of space to store the pointers and the count of zeros |

## Edge Cases Handled

- Array with no zeros
- Array with all zeros
- Array with zeros at the beginning or end

## What I Learned

How to efficiently duplicate zeros in an array by using two pointers to shift elements to the right

## Similar Problems

- Remove Element
- Move Zeroes

## Solution Code

```text
class Solution:
    def duplicateZeros(self, arr):
        zeros = arr.count(0)
        n = len(arr)
        
        i = n - 1
        j = n + zeros - 1
        
        while i < j:
            if j < n:
                arr[j] = arr[i]
            
            if arr[i] == 0:
                j -= 1
                if j < n:
                    arr[j] = 0
            
            i -= 1
            j -= 1
```
