# DI String Match

**Date:** 2026-07-18  
**Difficulty:** 🟢 **Easy**  
**Tags:** `Array` `Two Pointers` `String` `Greedy`

## Problem Description

A permutation perm of n + 1 integers of all the integers in the range [0, n] can be represented as a string s of length n where: s[i] == &#39;I&#39; if perm[i] < perm[i + 1] , and s[i] == &#39;D&#39; if perm[i] > perm[i + 1] . Given a string s , reconstruct the permutation perm and return it. If there are multiple valid permutations perm, return any of them . Example 1: Input: s = "IDID" Output: [0,4,1,3,2] Example 2: Input: s = "III" Output: [0,1,2,3] Example 3: Input: s = "DDI" Output: [3,2,0,1] Constraints: 1 <= s.length <= 10 5 s[i] is either &#39;I&#39; or &#39;D&#39; .

[LeetCode Link](https://leetcode.com/problems/di-string-match)

## Approach

Two Pointers

> Reconstruct permutation by iterating through string and adjusting pointers based on character values

## Solution Logic

1. Initialize low and high pointers
2. Iterate through string and append values based on character
3. Append remaining value after iteration

## Complexity Analysis

| Complexity | Analysis |
|------------|----------|
| **Time:** | O(n) — where n is the length of the string, as we only iterate through the string once |
| **Space:** | O(n) — where n is the length of the string, as we store the result in a list of the same length |

## Edge Cases Handled

- Empty string
- String with only 'I' or only 'D'

## What I Learned

Using two pointers to track the range of possible values and iterating through the string to reconstruct the permutation

## Similar Problems

- Next Greater Element
- Permutation Sequence

## Solution Code

```text
class Solution:
    def diStringMatch(self, s: str) -> List[int]:
        low=0
        high=len(s)
        ans=[]
        for ch in s:
            if ch=="I":
                ans.append(low)
                low+=1
            else:
                ans.append(high)
                high-=1
                
        ans.append(low)

        return ans
```
