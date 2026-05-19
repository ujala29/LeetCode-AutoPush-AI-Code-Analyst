# Length of Last Word

**Date:** 2026-05-19  
**Difficulty:** 🟢 **Easy**  
**Tags:** `String`

## Problem Description

Given a string s consisting of words and spaces, return the length of the last word in the string. A word is a maximal substring consisting of non-space characters only. Example 1: Input: s = &quot;Hello World&quot; Output: 5 Explanation: The last word is &quot;World&quot; with length 5. Example 2: Input: s = &quot; fly me to the moon &quot; Output: 4 Explanation: The last word is &quot;moon&quot; with length 4. Example 3: Input: s = &quot;luffy is still joyboy&quot; Output: 6 Explanation: The last word is &quot;joyboy&quot; with length 6. Constraints: 1 <= s.length <= 10 4 s consists of only 

[LeetCode Link](https://leetcode.com/problems/length-of-last-word)

## Approach

Two-Pointer Technique

> Iterate through the string from the end to find the length of the last word

## Solution Logic

1. Initialize variables to track the length and counting status
2. Iterate through the string from the end
3. Count characters until a space is encountered after a word

## Complexity Analysis

| Complexity | Analysis |
|------------|----------|
| **Time:** | O(n) — where n is the length of the string, as we potentially iterate through the entire string once |
| **Space:** | O(1) — as we only use a constant amount of space to store the length and counting status |

## Edge Cases Handled

- Empty string
- String with multiple spaces between words
- String with leading or trailing spaces

## What I Learned

The importance of handling edge cases and using a simple iterative approach to solve string problems

## Similar Problems

- Reverse Words in a String
- Valid Palindrome

## Solution Code

```text
class Solution {
public:
    int lengthOfLastWord(string s) {
        int length = 0;
        bool counting = false;
        
        for (int i = s.length() - 1; i >= 0; i--) {
            if (s[i] != ' ') {
                counting = true;
                length++;
            }
            else if (counting) {
                break;
            }
        }
        
        return length;
    }
};
```
