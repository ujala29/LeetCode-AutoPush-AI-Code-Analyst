# Sort Array By Parity

**Date:** 2026-07-17  
**Difficulty:** 🟢 **Easy**  
**Tags:** `Array` `Two Pointers` `Sorting`

## Problem Description

Given an integer array nums , move all the even integers at the beginning of the array followed by all the odd integers. Return any array that satisfies this condition . Example 1: Input: nums = [3,1,2,4] Output: [2,4,3,1] Explanation: The outputs [4,2,3,1], [2,4,1,3], and [4,2,1,3] would also be accepted. Example 2: Input: nums = [0] Output: [0] Constraints: 1 <= nums.length <= 5000 0 <= nums[i] <= 5000

[LeetCode Link](https://leetcode.com/problems/sort-array-by-parity)

## Approach

Two Pointers

> Separate even and odd numbers using two pointers

## Solution Logic

1. Initialize two pointers at the start and end of the array
2. Iterate through the array and place even numbers at the start and odd numbers at the end
3. Return the resulting array

## Complexity Analysis

| Complexity | Analysis |
|------------|----------|
| **Time:** | O(n) — where n is the number of elements in the array, because we are doing a single pass through the array |
| **Space:** | O(n) — where n is the number of elements in the array, because we are creating a new array of the same size |

## Edge Cases Handled

- Empty array
- Array with only one element
- Array with all even or all odd numbers

## What I Learned

Using two pointers can be an efficient way to solve problems that require separating or rearranging elements in an array

## Similar Problems

- Sort Colors
- Partition List

## Solution Code

```text
class Solution:
    def sortArrayByParity(self, nums: List[int]) -> List[int]:
        j=len(nums)-1
        i=0
        ans=[0]*len(nums)
        for m in range(0,len(nums)):
            if nums[m]%2==0:
                ans[i]=nums[m]
                i=i+1
            else:
                ans[j]=nums[m]
                j=j-1
        

        return ans


```
