# Is Subsequence

**Date:** 2026-07-17  
**Difficulty:** 🟢 **Easy**  
**Tags:** `Two Pointers` `String` `Dynamic Programming`

## Problem Description

Given two strings s and t , return true if s is a subsequence of t , or false otherwise . A subsequence of a string is a new string that is formed from the original string by deleting some (can be none) of the characters without disturbing the relative positions of the remaining characters. (i.e., &quot;ace&quot; is a subsequence of &quot; a b c d e &quot; while &quot;aec&quot; is not). Example 1: Input: s = "abc", t = "ahbgdc" Output: true Example 2: Input: s = "axc", t = "ahbgdc" Output: false Constraints: 0 <= s.length <= 100 0 <= t.length <= 10 4 s and t consist only of lowercase English l

[LeetCode Link](https://leetcode.com/problems/is-subsequence)

## Approach

Two Pointers

> Use two pointers to traverse both strings and check for subsequence

## Solution Logic

1. Initialize two pointers i and j to 0
2. Compare characters at i and j, increment i if they match and j if they don't
3. Return true if all characters in s are found in t, false otherwise

## Complexity Analysis

| Complexity | Analysis |
|------------|----------|
| **Time:** | O(n) — where n is the length of string t, because we are potentially scanning through the entire string t once |
| **Space:** | O(1) — because we are using a constant amount of space to store the pointers and variables |

## Edge Cases Handled

- empty string s
- empty string t
- s is longer than t

## What I Learned

The two pointers technique can be used to efficiently solve subsequence problems by avoiding unnecessary comparisons

## Similar Problems

- Longest Common Subsequence
- Shortest Common Supersequence

## Solution Code

```text
class Solution:
    def isSubsequence(self, s: str, t: str) -> bool:
        i,j=0,0
        while i<len(s) and j<len(t):
            if s[i]==t[j]:
                i+=1
                j+=1
            else:
                j+=1
        
        return i==len(s)
        
```
