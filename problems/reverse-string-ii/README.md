# Reverse String II

**Date:** 2026-07-17  
**Difficulty:** 🟢 **Easy**  
**Tags:** `Two Pointers` `String`

## Problem Description

Given a string s and an integer k , reverse the first k characters for every 2k characters counting from the start of the string. If there are fewer than k characters left, reverse all of them. If there are less than 2k but greater than or equal to k characters, then reverse the first k characters and leave the other as original. Example 1: Input: s = "abcdefg", k = 2 Output: "bacdfeg" Example 2: Input: s = "abcd", k = 2 Output: "bacd" Constraints: 1 <= s.length <= 10 4 s consists of only lowercase English letters. 1 <= k <= 10 4

[LeetCode Link](https://leetcode.com/problems/reverse-string-ii)

## Approach

Two Pointers and String Manipulation

> Reverse the first k characters for every 2k characters in a string

## Solution Logic

1. Iterate over the string in steps of 2k
2. Reverse the first k characters of each 2k block
3. Append the reversed and non-reversed parts to the result

## Complexity Analysis

| Complexity | Analysis |
|------------|----------|
| **Time:** | O(n) — where n is the length of the string, because we are scanning the string once |
| **Space:** | O(n) — where n is the length of the string, because we are storing the result in a new string |

## Edge Cases Handled

- When there are fewer than k characters left
- When there are less than 2k but greater than or equal to k characters left

## What I Learned

How to manipulate strings and use two pointers to solve a problem efficiently

## Similar Problems

- Reverse Words in a String
- Reverse Linked List

## Solution Code

```text
class Solution:
    def reverseStr(self, s: str, k: int) -> str:
        res = ""

        for i in range(0, len(s), 2*k):
            # reverse first k
            res += s[i:i+k][::-1]
            # keep next k as it is
            res += s[i+k:i+2*k]

        return res
```
