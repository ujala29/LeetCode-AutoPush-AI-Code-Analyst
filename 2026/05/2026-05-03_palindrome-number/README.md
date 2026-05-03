# Palindrome Number

**Date:** 2026-05-03  
**Difficulty:** 🟢 **Easy**  
**Tags:** `Math`

## Problem Description

Given an integer x , return true if x is a palindrome , and false otherwise . Example 1: Input: x = 121 Output: true Explanation: 121 reads as 121 from left to right and from right to left. Example 2: Input: x = -121 Output: false Explanation: From left to right, it reads -121. From right to left, it becomes 121-. Therefore it is not a palindrome. Example 3: Input: x = 10 Output: false Explanation: Reads 01 from right to left. Therefore it is not a palindrome. Constraints: -2 31 <= x <= 2 31 - 1 Follow up: Could you solve it without converting the integer to a string?

[LeetCode Link](https://leetcode.com/problems/palindrome-number)

## Approach

Half Reversal / Mathematical Digit Comparison

> Reverse only the second half of the number and compare with the first half to avoid overflow and extra space.

## Solution Logic

1. Step 1: Early return false for negative numbers and numbers ending in 0 (except 0 itself), since they can't be palindromes.
2. Step 2: Iteratively extract the last digit of x and build revertedNumber until revertedNumber >= x (meaning we've processed half the digits).
3. Step 3: Compare x == revertedNumber (even digit count) OR x == revertedNumber / 10 (odd digit count, middle digit discarded).

## Complexity Analysis

| Complexity | Analysis |
|------------|----------|
| **Time:** | O(log10(n)) — we only iterate through half the digits of the number |
| **Space:** | O(1) — only a constant amount of extra variables used, no string conversion |

## Edge Cases Handled

- Negative numbers (always false)
- Numbers ending in 0 but not equal to 0 (e.g., 10, 100 — always false)
- Single digit numbers (always true, loop never executes)
- Zero itself (returns true)
- Odd-length palindromes (middle digit handled by revertedNumber / 10)

## What I Learned

You don't need to reverse the entire number or convert to a string — reversing just the second half and comparing with the first half is sufficient, more efficient, and avoids integer overflow risks.

## Similar Problems

- Reverse Integer
- Valid Palindrome (String)
- Palindrome Linked List
- Find the Closest Palindrome
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
