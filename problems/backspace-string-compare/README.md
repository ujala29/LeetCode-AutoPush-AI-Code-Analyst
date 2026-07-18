# Backspace String Compare

**Date:** 2026-07-18  
**Difficulty:** 🟢 **Easy**  
**Tags:** `Two Pointers` `String` `Stack` `Simulation`

## Problem Description

Given two strings s and t , return true if they are equal when both are typed into empty text editors . &#39;#&#39; means a backspace character. Note that after backspacing an empty text, the text will continue empty. Example 1: Input: s = &quot;ab#c&quot;, t = &quot;ad#c&quot; Output: true Explanation: Both s and t become &quot;ac&quot;. Example 2: Input: s = &quot;ab##&quot;, t = &quot;c#d#&quot; Output: true Explanation: Both s and t become &quot;&quot;. Example 3: Input: s = &quot;a#c&quot;, t = &quot;b&quot; Output: false Explanation: s becomes &quot;c&quot; while t becomes &quot;b&quot;.

[LeetCode Link](https://leetcode.com/problems/backspace-string-compare)

## Approach

Two Pointers/Stack Simulation

> Compare two strings with backspace characters by simulating the backspace operation

## Solution Logic

1. Create a helper function to process each string
2. Use a stack to store characters and handle backspace operations
3. Compare the resulting stacks for both strings

## Complexity Analysis

| Complexity | Analysis |
|------------|----------|
| **Time:** | O(n + m) — where n and m are the lengths of the input strings, because we process each character in both strings once |
| **Space:** | O(n + m) — because in the worst case, we might store all characters from both strings in the stacks |

## Edge Cases Handled

- Empty strings
- Strings with only backspace characters
- Strings with backspace characters at the end

## What I Learned

Using a stack to simulate the backspace operation allows for efficient comparison of strings with backspace characters

## Similar Problems

- Valid Parentheses
- Basic Calculator

## Solution Code

```text
class Solution:
    def backspaceCompare(self, s: str, t: str) -> bool:
        
        def process_string(string):
            stack = []
            for char in string:
                if char != '#':
                    stack.append(char)
                elif stack:
                    stack.pop()
            return stack
        
        return process_string(s) == process_string(t)
```
