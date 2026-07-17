# Count Binary Substrings

**Date:** 2026-07-17  
**Difficulty:** 🟢 **Easy**  
**Tags:** `Two Pointers` `String`

## Problem Description

Given a binary string s , return the number of non-empty substrings that have the same number of 0 &#39;s and 1 &#39;s, and all the 0 &#39;s and all the 1 &#39;s in these substrings are grouped consecutively. Substrings that occur multiple times are counted the number of times they occur. Example 1: Input: s = &quot;00110011&quot; Output: 6 Explanation: There are 6 substrings that have equal number of consecutive 1&#39;s and 0&#39;s: &quot;0011&quot;, &quot;01&quot;, &quot;1100&quot;, &quot;10&quot;, &quot;0011&quot;, and &quot;01&quot;. Notice that some of these substrings repeat and are coun

[LeetCode Link](https://leetcode.com/problems/count-binary-substrings)

## Approach

Two Pointers

> Count binary substrings with consecutive 0's and 1's by tracking previous and current character counts

## Solution Logic

1. Initialize previous and current character counts
2. Iterate through the string, updating counts when characters change
3. Add the minimum of previous and current counts to the total count when characters change

## Complexity Analysis

| Complexity | Analysis |
|------------|----------|
| **Time:** | O(n) — where n is the length of the string, because we make a single pass through the string |
| **Space:** | O(1) — because we use a constant amount of space to store the counts and the result |

## Edge Cases Handled

- Empty string
- String with only one character

## What I Learned

To solve this problem, we need to keep track of the counts of consecutive characters and update the total count whenever the characters change

## Similar Problems

- Count Substrings with Only 1's
- Count Substrings with Equal Number of 0's and 1's

## Solution Code

```text
class Solution:
    def countBinarySubstrings(self, s: str) -> int:
        prev = 0
        curr = 1
        count = 0

        for i in range(1, len(s)):
            if s[i] == s[i-1]:
                curr += 1
            else:
                count += min(prev, curr)
                prev = curr
                curr = 1

        count += min(prev, curr)
        return count
```
