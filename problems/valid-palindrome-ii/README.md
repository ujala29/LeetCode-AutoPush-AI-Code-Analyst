# Valid Palindrome II

**Date:** 2026-07-17  
**Difficulty:** 🟢 **Easy**  
**Tags:** `Two Pointers` `String` `Greedy`

## Problem Description

Given a string s , return true if the s can be palindrome after deleting at most one character from it . Example 1: Input: s = &quot;aba&quot; Output: true Example 2: Input: s = &quot;abca&quot; Output: true Explanation: You could delete the character &#39;c&#39;. Example 3: Input: s = &quot;abc&quot; Output: false Constraints: 1 <= s.length <= 10 5 s consists of lowercase English letters.

[LeetCode Link](https://leetcode.com/problems/valid-palindrome-ii)

## Approach

Two Pointers

> Check if a string can be a palindrome after deleting at most one character

## Solution Logic

1. Initialize two pointers at the start and end of the string
2. Compare characters and move pointers towards the center
3. If a mismatch is found, check if the remaining substring is a palindrome after deleting one character

## Complexity Analysis

| Complexity | Analysis |
|------------|----------|
| **Time:** | O(n) — where n is the length of the string, because we potentially traverse the string twice |
| **Space:** | O(1) — because we only use a constant amount of space to store the pointers and other variables |

## Edge Cases Handled

- Empty string
- Single character string
- String with only two characters

## What I Learned

The importance of checking edge cases and using a helper function to simplify the code

## Similar Problems

- Valid Palindrome
- Longest Palindromic Substring

## Solution Code

```text
class Solution:
    def validPalindrome(self, s: str) -> bool:
        
        def isPalindrome(i, j):
            while i < j:
                if s[i] != s[j]:
                    return False
                i += 1
                j -= 1
            return True
        
        i = 0
        j = len(s) - 1
        
        while i < j:
            if s[i] == s[j]:
                i += 1
                j -= 1
            else:
                return isPalindrome(i+1, j) or isPalindrome(i, j-1)
        
        return True
```
