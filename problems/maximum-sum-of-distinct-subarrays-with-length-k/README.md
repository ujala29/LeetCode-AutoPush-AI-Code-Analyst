# Maximum Sum of Distinct Subarrays With Length K

**Date:** 2026-08-01  
**Difficulty:** 🟡 **Medium**  
**Tags:** `Array` `Hash Table` `Sliding Window`

## Problem Description

You are given an integer array nums and an integer k . Find the maximum subarray sum of all the subarrays of nums that meet the following conditions: The length of the subarray is k , and All the elements of the subarray are distinct . Return the maximum subarray sum of all the subarrays that meet the conditions . If no subarray meets the conditions, return 0 . A subarray is a contiguous non-empty sequence of elements within an array. Example 1: Input: nums = [1,5,4,2,9,9,9], k = 3 Output: 15 Explanation: The subarrays of nums with length 3 are: - [1,5,4] which meets the requirements and has a

[LeetCode Link](https://leetcode.com/problems/maximum-sum-of-distinct-subarrays-with-length-k)

## Approach

Sliding Window with Hash Set

> Use a sliding window with a hash set to efficiently track distinct subarrays of length k and calculate their sums

## Solution Logic

1. remove duplicates from the current window
2. add the current element to the window
3. check if the window size equals k and update the maximum sum

## Complexity Analysis

| Complexity | Analysis |
|------------|----------|
| **Time:** | O(n) — where n is the number of elements in the input array, because each element is visited at most twice |
| **Space:** | O(k) — where k is the size of the sliding window, because in the worst case, the hash set will store k distinct elements |

## Edge Cases Handled

- empty input array
- k larger than the input array length
- no distinct subarrays of length k

## What I Learned

The importance of using a sliding window approach with a hash set to efficiently solve problems involving distinct subarrays

## Similar Problems

- Longest Substring Without Repeating Characters
- Subarray Sum Equals K

## Solution Code

```text
class Solution:
    def maximumSubarraySum(self, nums: List[int], k: int) -> int:
        
        sum = 0
        maxsum = 0
        s = set()

        i = 0
        j = 0

        while j < len(nums):

            # Step 1: remove duplicates
            while nums[j] in s:
                s.remove(nums[i])
                sum -= nums[i]
                i += 1

            # Step 2: add current element
            s.add(nums[j])
            sum += nums[j]

            # Step 3: check window size
            if j - i + 1 == k:
                maxsum = max(maxsum, sum)

                # slide window
                s.remove(nums[i])
                sum -= nums[i]
                i += 1

            j += 1

        return maxsum
```
