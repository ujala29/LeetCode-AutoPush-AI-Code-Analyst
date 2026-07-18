# Sort Array By Parity II

**Date:** 2026-07-18  
**Difficulty:** 🟢 **Easy**  
**Tags:** `Array` `Two Pointers` `Sorting`

## Problem Description

Given an array of integers nums , half of the integers in nums are odd , and the other half are even . Sort the array so that whenever nums[i] is odd, i is odd , and whenever nums[i] is even, i is even . Return any answer array that satisfies this condition . Example 1: Input: nums = [4,2,5,7] Output: [4,5,2,7] Explanation: [4,7,2,5], [2,5,4,7], [2,7,4,5] would also have been accepted. Example 2: Input: nums = [2,3] Output: [2,3] Constraints: 2 <= nums.length <= 2 * 10 4 nums.length is even. Half of the integers in nums are even. 0 <= nums[i] <= 1000 Follow Up: Could you solve it in-place?

[LeetCode Link](https://leetcode.com/problems/sort-array-by-parity-ii)

## Approach

Two Pointers

> Swap odd numbers at even indices with even numbers at odd indices

## Solution Logic

1. Initialize two pointers at even and odd indices
2. Check if the number at the even index is odd
3. If odd, swap with the number at the odd index and move both pointers

## Complexity Analysis

| Complexity | Analysis |
|------------|----------|
| **Time:** | O(n) — where n is the number of elements in the input array, because we are potentially scanning the entire array once |
| **Space:** | O(1) — because we are modifying the input array in-place and using a constant amount of space |

## Edge Cases Handled

- Empty array
- Array with single element

## What I Learned

To solve this problem, we need to carefully consider the parity of both the index and the value at that index, and use two pointers to efficiently swap the elements

## Similar Problems

- Sort Array By Parity
- Partition Array Into Disjoint Intervals

## Solution Code

```text
class Solution:
    def sortArrayByParityII(self, nums: List[int]) -> List[int]:
        i=0
        j=1
        while i <len(nums) and j< len(nums):
            if nums[i]%2!=0:
                nums[i],nums[j]=nums[j],nums[i]
                if nums[i]%2==0:
                    i+=2
                elif nums[j]%2!=0:
                    j+=2
            else:
                i+=2
        return nums    
```
