# Reverse Only Letters

**Date:** 2026-07-18  
**Difficulty:** 🟢 **Easy**  
**Tags:** `Two Pointers` `String`

## Problem Description

Given a string s , reverse the string according to the following rules: All the characters that are not English letters remain in the same position. All the English letters (lowercase or uppercase) should be reversed. Return s after reversing it . Example 1: Input: s = "ab-cd" Output: "dc-ba" Example 2: Input: s = "a-bC-dEf-ghIj" Output: "j-Ih-gfE-dCba" Example 3: Input: s = "Test1ng-Leet=code-Q!" Output: "Qedo1ct-eeLg=ntse-T!" Constraints: 1 <= s.length <= 100 s consists of characters with ASCII values in the range [33, 122] . s does not contain &#39;\&quot;&#39; or &#39;\\&#39; .

[LeetCode Link](https://leetcode.com/problems/reverse-only-letters)

## Approach

Two Pointers

> Reverse English letters in a string while keeping non-letters in place

## Solution Logic

1. Convert the string to a list for mutable operations
2. Initialize two pointers at the start and end of the list
3. Swap letters at the pointers if both are letters, otherwise move the pointer that points to a non-letter

## Complexity Analysis

| Complexity | Analysis |
|------------|----------|
| **Time:** | O(n) — where n is the length of the string, because we potentially visit each character once |
| **Space:** | O(n) — because we convert the string to a list, which requires additional space proportional to the length of the string |

## Edge Cases Handled

- Empty string
- String with no letters
- String with only letters

## What I Learned

Using two pointers can efficiently solve problems that require comparing or swapping elements from opposite ends of a sequence

## Similar Problems

- Reverse String
- Valid Palindrome

## Solution Code

```text
class Solution:
    def reverseOnlyLetters(self, s: str) -> str:
        s = list(s)   # 🔥 convert to list
        
        i = 0
        j = len(s) - 1
        
        while i < j:
            if s[i].isalpha() and s[j].isalpha():
                s[i], s[j] = s[j], s[i]   # swap
                i += 1
                j -= 1
            elif not s[i].isalpha():
                i += 1
            else:
                j -= 1
        
        return "".join(s)   # 🔥 convert back to string
```
