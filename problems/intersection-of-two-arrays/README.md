# Intersection of Two Arrays

**Date:** 2026-07-17  
**Difficulty:** 🟢 **Easy**  
**Tags:** `Array` `Hash Table` `Two Pointers` `Binary Search` `Sorting`

## Problem Description

Given two integer arrays nums1 and nums2 , return an array of their intersection . Each element in the result must be unique and you may return the result in any order . Example 1: Input: nums1 = [1,2,2,1], nums2 = [2,2] Output: [2] Example 2: Input: nums1 = [4,9,5], nums2 = [9,4,9,8,4] Output: [9,4] Explanation: [4,9] is also accepted. Constraints: 1 <= nums1.length, nums2.length <= 1000 0 <= nums1[i], nums2[i] <= 1000

[LeetCode Link](https://leetcode.com/problems/intersection-of-two-arrays)

## Approach

Two Pointers with Sorting and Set

> Find unique intersection of two arrays using sorted sets and two pointers

## Solution Logic

1. Convert input arrays to sets to remove duplicates
2. Sort the sets
3. Initialize two pointers to traverse the sorted sets
4. Compare elements at the pointers and add to result if equal

## Complexity Analysis

| Complexity | Analysis |
|------------|----------|
| **Time:** | O(n log n + m log m) — due to sorting the sets of size n and m |
| **Space:** | O(n + m) — for storing the sets and the result |

## Edge Cases Handled

- Empty input arrays
- Arrays with duplicate elements

## What I Learned

Using sets to remove duplicates and sorting to enable efficient two-pointer traversal

## Similar Problems

- Intersection of Two Arrays II
- Find the Difference

## Solution Code

```text
class Solution:
    def intersection(self, nums1: List[int], nums2: List[int]) -> List[int]:
        
        n1=sorted(set(nums1))
        n2=sorted(set(nums2))
        i=0
        j=0
        ans=[]
        while i<len(n1) and j<len(n2):
            if n1[i]==n2[j]:
                ans.append(n1[i])
                i+=1
                j+=1
            elif n1[i]>n2[j]:
                j+=1
            else:
                i+=1
        return ans
```
