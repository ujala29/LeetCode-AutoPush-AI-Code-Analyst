# Shortest Distance to a Character

**Date:** 2026-07-17  
**Difficulty:** 🟢 **Easy**  
**Tags:** `Array` `Two Pointers` `String`

## Problem Description

Given a string s and a character c that occurs in s , return an array of integers answer where answer.length == s.length and answer[i] is the distance from index i to the closest occurrence of character c in s . The distance between two indices i and j is abs(i - j) , where abs is the absolute value function. Example 1: Input: s = &quot;loveleetcode&quot;, c = &quot;e&quot; Output: [3,2,1,0,1,0,0,1,2,2,1,0] Explanation: The character &#39;e&#39; appears at indices 3, 5, 6, and 11 (0-indexed). The closest occurrence of &#39;e&#39; for index 0 is at index 3, so the distance is abs(0 - 3) = 3. Th

[LeetCode Link](https://leetcode.com/problems/shortest-distance-to-a-character)

## Approach

Two Pass Approach

> Calculate shortest distance to a character in a string by making two passes from left to right and right to left

## Solution Logic

1. Initialize answer array and previous occurrence index
2. Make first pass from left to right to calculate distance to previous occurrence
3. Make second pass from right to left to update distance to closest occurrence

## Complexity Analysis

| Complexity | Analysis |
|------------|----------|
| **Time:** | O(n) — where n is the length of the string, because we make two passes through the string |
| **Space:** | O(n) — where n is the length of the string, because we need to store the answer array |

## Edge Cases Handled

- Empty string
- Character not found in string

## What I Learned

To solve this problem, we need to think about how to efficiently calculate the shortest distance to a character in a string, and the two pass approach is a good solution

## Similar Problems

- Minimum Distance to a Character
- Shortest Distance to a Target

## Solution Code

```text
class Solution:
    def shortestToChar(self, s: str, c: str):
        n = len(s)
        ans = [0] * n
        
        # Pass 1: Left → Right
        prev = float('-inf')
        for i in range(n):
            if s[i] == c:
                prev = i
            ans[i] = i - prev
        
        # Pass 2: Right → Left
        prev = float('inf')
        for i in range(n-1, -1, -1):
            if s[i] == c:
                prev = i
            ans[i] = min(ans[i], prev - i)
        
        return ans
```
