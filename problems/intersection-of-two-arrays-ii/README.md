# Intersection of Two Arrays II

**Date:** 2026-07-17  
**Difficulty:** 🟢 **Easy**  
**Tags:** `Array` `Hash Table` `Two Pointers` `Binary Search` `Sorting`

## Problem Description

Given two integer arrays nums1 and nums2 , return an array of their intersection . Each element in the result must appear as many times as it shows in both arrays and you may return the result in any order . Example 1: Input: nums1 = [1,2,2,1], nums2 = [2,2] Output: [2,2] Example 2: Input: nums1 = [4,9,5], nums2 = [9,4,9,8,4] Output: [4,9] Explanation: [9,4] is also accepted. Constraints: 1 <= nums1.length, nums2.length <= 1000 0 <= nums1[i], nums2[i] <= 1000 Follow up: What if the given array is already sorted? How would you optimize your algorithm? What if nums1 &#39;s size is small compared

[LeetCode Link](https://leetcode.com/problems/intersection-of-two-arrays-ii)

## Approach

Two Pointers

> Return intersection of two arrays with duplicate counts preserved

## Solution Logic

1. Sort both input arrays
2. Initialize two pointers to traverse both arrays
3. Compare elements at current pointers and append to result if they match

## Complexity Analysis

| Complexity | Analysis |
|------------|----------|
| **Time:** | O(n log n + m log m) — due to sorting both input arrays of lengths n and m |
| **Space:** | O(n + m) — for sorting and storing the result |

## Edge Cases Handled

- Empty input arrays
- Arrays with no common elements

## What I Learned

Using two pointers to traverse sorted arrays can efficiently find common elements while preserving their counts

## Similar Problems

- Intersection of Two Arrays
- Find Common Characters

## Solution Code

```text
class Solution:
    def intersect(self, nums1: List[int], nums2: List[int]) -> List[int]:
         
        n1=sorted((nums1))
        n2=sorted((nums2))
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
