# Longest Substring Without Repeating Characters

**Date:** 2026-08-04  
**Difficulty:** 🟡 **Medium**  
**Tags:** `Hash Table` `String` `Sliding Window`

## Problem Description

Given a string s , find the length of the longest substring without duplicate characters. Example 1: Input: s = &quot;abcabcbb&quot; Output: 3 Explanation: The answer is &quot;abc&quot;, with the length of 3. Note that &quot;bca&quot; and &quot;cab&quot; are also correct answers. Example 2: Input: s = &quot;bbbbb&quot; Output: 1 Explanation: The answer is &quot;b&quot;, with the length of 1. Example 3: Input: s = &quot;pwwkew&quot; Output: 3 Explanation: The answer is &quot;wke&quot;, with the length of 3. Notice that the answer must be a substring, &quot;pwke&quot; is a subsequence and not a 

[LeetCode Link](https://leetcode.com/problems/longest-substring-without-repeating-characters)

## Approach

Sliding Window with Hash Table

> Use a sliding window to track the longest substring without repeating characters

## Solution Logic

1. Initialize a hash table to store characters and their indices
2. Expand the window to the right and update the hash table
3. Shrink the window from the left when a repeating character is found

## Complexity Analysis

| Complexity | Analysis |
|------------|----------|
| **Time:** | O(n) — where n is the length of the string, because each character is visited at most twice |
| **Space:** | O(min(n, m)) — where m is the size of the character set, because in the worst case, the hash table will store all unique characters |

## Edge Cases Handled

- empty string
- string with all repeating characters

## What I Learned

The importance of using a hash table to efficiently track unique characters in a sliding window

## Similar Problems

- Longest Substring with At Most K Distinct Characters
- Subarrays with K Different Integers

## Solution Code

```text
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        map={}
        i=j=0
        maxlen=0
        while j<len(s):
            if map.get(s[j]) is not None:
                if map[s[j]] >= i:
                    i = map[s[j]] + 1
    

                

            map[s[j]]=j
            maxlen=max(maxlen,j-i+1)
            j=j+1
        
        return maxlen

            

        
```
