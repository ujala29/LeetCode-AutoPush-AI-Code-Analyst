# Two Sum

**Date:** 2026-05-18  
**Difficulty:** 🟢 **Easy**  
**Tags:** `Array` `Hash Table`

## Problem Description

Given an array of integers nums and an integer target , return indices of the two numbers such that they add up to target . You may assume that each input would have exactly one solution , and you may not use the same element twice. You can return the answer in any order. Example 1: Input: nums = [2,7,11,15], target = 9 Output: [0,1] Explanation: Because nums[0] + nums[1] == 9, we return [0, 1]. Example 2: Input: nums = [3,2,4], target = 6 Output: [1,2] Example 3: Input: nums = [3,3], target = 6 Output: [0,1] Constraints: 2 <= nums.length <= 10 4 -10 9 <= nums[i] <= 10 9 -10 9 <= target <= 10 

[LeetCode Link](https://leetcode.com/problems/two-sum)

## Approach

Brute Force

> Iterate through all pairs of numbers to find the target sum

## Solution Logic

1. Initialize two nested loops to iterate through the array
2. Check if the sum of the current pair equals the target
3. Return the indices of the pair if the sum matches the target

## Complexity Analysis

| Complexity | Analysis |
|------------|----------|
| **Time:** | O(n^2) — due to the nested loops iterating through the array |
| **Space:** | O(1) — excluding the space required for the output, the algorithm uses a constant amount of space |

## Edge Cases Handled

- Empty array
- No solution found

## What I Learned

The importance of considering the time complexity of an algorithm, as this brute force approach may not be efficient for large inputs

## Similar Problems

- 3Sum
- 4Sum

## Solution Code

```text
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        int n = nums.size();
        for (int i = 0; i < n - 1; i++) {
            for (int j = i + 1; j < n; j++) {
                if (nums[i] + nums[j] == target) {
                    return {i, j};
                }
            }
        }
        return {}; // No solution found
    }
};
```
