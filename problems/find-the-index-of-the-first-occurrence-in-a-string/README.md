# Find the Index of the First Occurrence in a String

**Date:** 2026-07-11  
**Difficulty:** 🟢 **Easy**  
**Tags:** `Two Pointers` `String` `String Matching`

## Problem Description

Given two strings needle and haystack , return the index of the first occurrence of needle in haystack , or -1 if needle is not part of haystack . Example 1: Input: haystack = &quot;sadbutsad&quot;, needle = &quot;sad&quot; Output: 0 Explanation: &quot;sad&quot; occurs at index 0 and 6. The first occurrence is at index 0, so we return 0. Example 2: Input: haystack = &quot;leetcode&quot;, needle = &quot;leeto&quot; Output: -1 Explanation: &quot;leeto&quot; did not occur in &quot;leetcode&quot;, so we return -1. Constraints: 1 <= haystack.length, needle.length <= 10 4 haystack and needle consist

[LeetCode Link](https://leetcode.com/problems/find-the-index-of-the-first-occurrence-in-a-string)

## Approach

Built-in String Method

> Utilize Python's built-in string method to find the index of the first occurrence of a substring

## Solution Logic

1. Define the function strStr with parameters haystack and needle
2. Use the find method of the haystack string to get the index of the first occurrence of needle
3. Return the index, or -1 if needle is not found

## Complexity Analysis

| Complexity | Analysis |
|------------|----------|
| **Time:** | O(n) — where n is the length of the haystack string, because in the worst case the find method has to scan the entire string |
| **Space:** | O(1) — because the find method does not use any additional space that scales with the input size |

## Edge Cases Handled

- empty needle
- needle not found in haystack
- needle is the same as haystack

## What I Learned

Python's built-in string methods can greatly simplify string manipulation tasks

## Similar Problems

- Find the Index of the Last Occurrence in a String
- Check if a String Contains a Substring

## Solution Code

```text
class Solution:
    def strStr(self, haystack: str, needle: str) -> int:
        return haystack.find(needle)
```
