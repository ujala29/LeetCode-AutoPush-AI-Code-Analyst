# Reverse Words in a String III

**Date:** 2026-07-17  
**Difficulty:** 🟢 **Easy**  
**Tags:** `Two Pointers` `String`

## Problem Description

Given a string s , reverse the order of characters in each word within a sentence while still preserving whitespace and initial word order. Example 1: Input: s = &quot;Let&#39;s take LeetCode contest&quot; Output: &quot;s&#39;teL ekat edoCteeL tsetnoc&quot; Example 2: Input: s = &quot;Mr Ding&quot; Output: &quot;rM gniD&quot; Constraints: 1 <= s.length <= 5 * 10 4 s contains printable ASCII characters. s does not contain any leading or trailing spaces. There is at least one word in s . All the words in s are separated by a single space.

[LeetCode Link](https://leetcode.com/problems/reverse-words-in-a-string-iii)

## Approach

Two Pointers

> Reverse each word in a string while preserving whitespace and initial word order

## Solution Logic

1. Initialize two pointers to track the start and end of each word
2. Reverse the characters in each word using slicing
3. Append the reversed word to the result string and add a space if necessary

## Complexity Analysis

| Complexity | Analysis |
|------------|----------|
| **Time:** | O(n) — where n is the length of the input string, because we are scanning the string once |
| **Space:** | O(n) — where n is the length of the input string, because we are creating a new string to store the result |

## Edge Cases Handled

- Empty string
- Single word
- Multiple words with varying lengths

## What I Learned

How to use two pointers to track the start and end of each word in a string and reverse the characters in each word

## Similar Problems

- Reverse String
- Reverse Vowels in a String

## Solution Code

```text
class Solution:
    def reverseWords(self, s: str) -> str:
        ans=""
        i=0
        while i<len(s):
            j=i
            while j <len(s) and s[j]!=" ":
                j=j+1
            

            ans+=s[i:j][::-1]
            if j<len(s):
                 ans+=" "
            i=j+1
        
        return ans
```
