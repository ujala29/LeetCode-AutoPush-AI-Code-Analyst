# Divide Two Integers

**Date:** 2026-07-23  
**Difficulty:** 🟡 **Medium**  
**Tags:** `Math` `Bit Manipulation`

## Problem Description

Given two integers dividend and divisor , divide two integers without using multiplication, division, and mod operator. The integer division should truncate toward zero, which means losing its fractional part. For example, 8.345 would be truncated to 8 , and -2.7335 would be truncated to -2 . Return the quotient after dividing dividend by divisor . Note: Assume we are dealing with an environment that could only store integers within the 32-bit signed integer range: [&minus;2 31 , 2 31 &minus; 1] . For this problem, if the quotient is strictly greater than 2 31 - 1 , then return 2 31 - 1 , and 

[LeetCode Link](https://leetcode.com/problems/divide-two-integers)

## Approach

Bit Manipulation

> Divide two integers without using multiplication, division, and mod operator by utilizing bit shifting

## Solution Logic

1. Determine the sign of the result by checking if exactly one of the dividend and divisor is negative
2. Use bit shifting to repeatedly subtract the divisor from the dividend and accumulate the result
3. Handle edge cases such as division by 1, division by self, and overflow

## Complexity Analysis

| Complexity | Analysis |
|------------|----------|
| **Time:** | O(log N) — where N is the absolute value of the dividend, because we are essentially performing a binary search to find the largest multiple of the divisor that is less than or equal to the dividend |
| **Space:** | O(1) — because we only use a constant amount of space to store the result and temporary variables |

## Edge Cases Handled

- division by 1
- division by self
- overflow
- underflow

## What I Learned

How to use bit manipulation to perform division without using the division operator, and how to handle edge cases to ensure the result is accurate and within the valid range

## Similar Problems

- Multiply Strings
- Pow(x, n)

## Solution Code

```text
class Solution:
    def divide(self, dividend: int, divisor: int) -> int:
        if dividend == divisor:
            return 1
        if dividend == -2**31 and divisor == -1:
            return (2**31) - 1 
        
        if divisor == 1:
            return dividend
        
        sign = -1 if (dividend < 0) ^ (divisor < 0) else 1
        
        n, d = abs(dividend), abs(divisor)
        ans = 0

        while n >= d:
            p = 0
            while n >= (d << p):
                p += 1
            
            p -= 1
            n -= (d << p)
            ans += (1 << p)

        return min(max(sign * ans, -2**31), 2**31 - 1)
```
