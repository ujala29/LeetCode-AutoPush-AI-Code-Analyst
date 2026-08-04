# Maximum Number of Vowels in a Substring of Given Length

**Date:** 2026-08-04  
**Difficulty:** 🟡 **Medium**  
**Tags:** `String` `Sliding Window`

## Problem Description

Given a string s and an integer k , return the maximum number of vowel letters in any substring of s with length k . Vowel letters in English are &#39;a&#39; , &#39;e&#39; , &#39;i&#39; , &#39;o&#39; , and &#39;u&#39; . Example 1: Input: s = &quot;abciiidef&quot;, k = 3 Output: 3 Explanation: The substring &quot;iii&quot; contains 3 vowel letters. Example 2: Input: s = &quot;aeiou&quot;, k = 2 Output: 2 Explanation: Any substring of length 2 contains 2 vowels. Example 3: Input: s = &quot;leetcode&quot;, k = 3 Output: 2 Explanation: &quot;lee&quot;, &quot;eet&quot; and &quot;ode&quot; contain 2

[LeetCode Link](https://leetcode.com/problems/maximum-number-of-vowels-in-a-substring-of-given-length)

## Approach

Sliding Window

> Use a sliding window to track the maximum number of vowels in a substring of given length

## Solution Logic

1. Initialize a window of size k
2. Count the vowels in the window
3. Slide the window to the right and update the count

## Complexity Analysis

| Complexity | Analysis |
|------------|----------|
| **Time:** | O(n) — where n is the length of the string, because we are scanning the string once |
| **Space:** | O(1) — because we are using a constant amount of space to store the count and the window boundaries |

## Edge Cases Handled

- Empty string
- k larger than the string length

## What I Learned

The sliding window technique can be used to efficiently solve problems that involve finding a maximum or minimum value in a substring of a given length

## Similar Problems

- Longest Substring Without Repeating Characters
- Minimum Window Substring

## Solution Code

```text
class Solution:
    def isvowel(self,c) ->bool:
         
        if c=="a" or c=="e" or c=="i" or c=="o" or c=="u":
             return True
        return False 
    def maxVowels(self, s: str, k: int) -> int:

        maxcount=0
        count=0
        i=j=0
        while j<len(s):
            if self.isvowel(s[j]):
                count+=1
            
            if j-i+1==k:
                maxcount=max(count,maxcount)
                if self.isvowel(s[i]):
                    count-=1
                i+=1
            j+=1
        
        return maxcount

            

        

        
```
