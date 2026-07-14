# Reverse String

**Date:** 2026-07-14  
**Difficulty:** 🟢 **Easy**  
**Tags:** `Two Pointers` `String`

## Problem Description

Write a function that reverses a string. The input string is given as an array of characters s . You must do this by modifying the input array in-place with O(1) extra memory. Example 1: Input: s = ["h","e","l","l","o"] Output: ["o","l","l","e","h"] Example 2: Input: s = ["H","a","n","n","a","h"] Output: ["h","a","n","n","a","H"] Constraints: 1 <= s.length <= 10 5 s[i] is a printable ascii character .

[LeetCode Link](https://leetcode.com/problems/reverse-string)

## Approach

Two Pointers

> Reverse a string in-place using two pointers

## Solution Logic

1. Initialize two pointers at the start and end of the string
2. Swap characters at the two pointers
3. Move pointers towards the center of the string

## Complexity Analysis

| Complexity | Analysis |
|------------|----------|
| **Time:** | O(n) — where n is the length of the string, because we are scanning the string once |
| **Space:** | O(1) — because we are modifying the input array in-place with no extra memory |

## Edge Cases Handled

- Empty string
- String with single character

## What I Learned

How to reverse a string in-place using two pointers, which is an efficient and common technique in string manipulation problems

## Similar Problems

- Reverse Linked List
- Rotate Array

## Solution Code

```text
class Solution:
    def reverseString(self, s: List[str]) -> None:
        """
        Do not return anything, modify s in-place instead.
        """
        i=0
        j=len(s)-1
        while(i<=j):

            t=s[i]
            s[i]=s[j]
            s[j]=t
            i+=1
            j-=1
        
```
