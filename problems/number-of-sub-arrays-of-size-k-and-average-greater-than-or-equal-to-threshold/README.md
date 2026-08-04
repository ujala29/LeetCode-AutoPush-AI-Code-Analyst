# Number of Sub-arrays of Size K and Average Greater than or Equal to Threshold

**Date:** 2026-08-04  
**Difficulty:** 🟡 **Medium**  
**Tags:** `Array` `Sliding Window`

## Problem Description

Given an array of integers arr and two integers k and threshold , return the number of sub-arrays of size k and average greater than or equal to threshold . Example 1: Input: arr = [2,2,2,2,5,5,5,8], k = 3, threshold = 4 Output: 3 Explanation: Sub-arrays [2,5,5],[5,5,5] and [5,5,8] have averages 4, 5 and 6 respectively. All other sub-arrays of size 3 have averages less than 4 (the threshold). Example 2: Input: arr = [11,13,17,23,29,31,7,5,2,3], k = 3, threshold = 5 Output: 6 Explanation: The first 6 sub-arrays of size 3 have averages greater than 5. Note that averages are not integers. Constra

[LeetCode Link](https://leetcode.com/problems/number-of-sub-arrays-of-size-k-and-average-greater-than-or-equal-to-threshold)

## Approach

Sliding Window

> Count sub-arrays of size k with average greater than or equal to threshold using a sliding window approach

## Solution Logic

1. Initialize variables to track the sum and count of sub-arrays
2. Expand the window to the right by adding elements to the sum
3. Shrink the window from the left by subtracting elements from the sum when the window size reaches k

## Complexity Analysis

| Complexity | Analysis |
|------------|----------|
| **Time:** | O(n) — where n is the number of elements in the array, because we make a single pass through the array |
| **Space:** | O(1) — because we use a constant amount of space to store the sum, count, and window boundaries |

## Edge Cases Handled

- Empty array
- k larger than array length
- Threshold greater than maximum possible average

## What I Learned

The sliding window technique can be used to efficiently solve problems involving sub-arrays or sub-strings with certain properties

## Similar Problems

- Maximum Average Subarray
- Subarray Sum Equals K

## Solution Code

```text
class Solution:
    def numOfSubarrays(self, arr: List[int], k: int, threshold: int) -> int:
       count = sum = i = j = 0
       avg=0

       while j<len(arr):
            sum+=arr[j]

            if j-i+1==k:
                avg=sum/k
                if avg>=threshold:
                    count+=1
                sum-=arr[i]
                i+=1

            j+=1
       return count



        
```
