# Long Pressed Name

**Date:** 2026-07-18  
**Difficulty:** 🟢 **Easy**  
**Tags:** `Two Pointers` `String`

## Problem Description

Your friend is typing his name into a keyboard. Sometimes, when typing a character c , the key might get long pressed , and the character will be typed 1 or more times. You examine the typed characters of the keyboard. Return True if it is possible that it was your friends name, with some characters (possibly none) being long pressed. Example 1: Input: name = &quot;alex&quot;, typed = &quot;aaleex&quot; Output: true Explanation: &#39;a&#39; and &#39;e&#39; in &#39;alex&#39; were long pressed. Example 2: Input: name = &quot;saeed&quot;, typed = &quot;ssaaedd&quot; Output: false Explanation: &#3

[LeetCode Link](https://leetcode.com/problems/long-pressed-name)

## Approach

Two Pointers

> Check if typed string can be formed by long pressing characters in the name string

## Solution Logic

1. Initialize two pointers for name and typed strings
2. Compare characters at current positions and move pointers accordingly
3. Handle cases where characters do not match but previous character in name matches current character in typed

## Complexity Analysis

| Complexity | Analysis |
|------------|----------|
| **Time:** | O(n + m) — where n and m are lengths of name and typed strings respectively, because we are scanning both strings once |
| **Space:** | O(1) — because we are using a constant amount of space to store pointers and variables |

## Edge Cases Handled

- Empty strings
- Strings with repeated characters
- Strings with different lengths

## What I Learned

How to use two pointers to compare strings and handle edge cases where characters do not match

## Similar Problems

- Valid Palindrome
- Compare Strings

## Solution Code

```text
class Solution:
    def isLongPressedName(self, name: str, typed: str) -> bool:
        i=0
        j=0
        while i< len(name) and j < len(typed):
            if name[i]==typed[j]:
                i+=1
                j+=1
            elif i>0 and name[i-1] ==typed[j]:
                j+=1
            
            elif name[i] !=typed[j]:
                return False
        
        while j< len(typed):
            if name[i-1]==typed[j]:
                j+=1
            else:
                return False
        return i==len(name) and j==len(typed)
        
```
