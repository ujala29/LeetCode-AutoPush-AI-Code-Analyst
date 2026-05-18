# Palindrome Number

**Date:** 2026-05-18  
**Difficulty:** 🟢 **Easy**  
**Tags:** `Math`

## Problem Description

Given an integer x , return true if x is a palindrome , and false otherwise . Example 1: Input: x = 121 Output: true Explanation: 121 reads as 121 from left to right and from right to left. Example 2: Input: x = -121 Output: false Explanation: From left to right, it reads -121. From right to left, it becomes 121-. Therefore it is not a palindrome. Example 3: Input: x = 10 Output: false Explanation: Reads 01 from right to left. Therefore it is not a palindrome. Constraints: -2 31 <= x <= 2 31 - 1 Follow up: Could you solve it without converting the integer to a string?

[LeetCode Link](https://leetcode.com/problems/palindrome-number)

## Approach

Two Pointers and Reversal

> Check if an integer is a palindrome by reversing half of it

## Solution Logic

1. Check for negative numbers and numbers ending with 0
2. Reverse half of the number
3. Compare the reversed half with the original half

## Complexity Analysis

| Complexity | Analysis |
|------------|----------|
| **Time:** | O(log n) — because we are reversing half of the number, which takes logarithmic time |
| **Space:** | O(1) — because we are using a constant amount of space to store the reversed number |

## Edge Cases Handled

- Negative numbers
- Numbers ending with 0

## What I Learned

To solve this problem, we need to handle edge cases and reverse half of the number to compare it with the original half

## Similar Problems

- Valid Palindrome
- Palindrome Partitioning

## Solution Code

```text
class Solution {
public:
    bool isPalindrome(int x) {
        if (x < 0 || (x % 10 == 0 && x != 0)) {
            return false;
        }
        int revertedNumber = 0;
        while (x > revertedNumber) {
            revertedNumber = revertedNumber * 10 + x % 10;
            x /= 10;
        }
        return x == revertedNumber || x == revertedNumber / 10;
    }
};
```
