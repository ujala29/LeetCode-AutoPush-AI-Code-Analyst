# Reverse Integer

**Date:** 2026-07-08  
**Difficulty:** 🟡 **Medium**  
**Tags:** `Math`

## Problem Description

Given a signed 32-bit integer x , return x with its digits reversed . If reversing x causes the value to go outside the signed 32-bit integer range [-2 31 , 2 31 - 1] , then return 0 . Assume the environment does not allow you to store 64-bit integers (signed or unsigned). Example 1: Input: x = 123 Output: 321 Example 2: Input: x = -123 Output: -321 Example 3: Input: x = 120 Output: 21 Constraints: -2 31 <= x <= 2 31 - 1

[LeetCode Link](https://leetcode.com/problems/reverse-integer)

## Approach

Math/Modular Arithmetic

> Reverse integer by iteratively appending digits while checking for overflow

## Solution Logic

1. Extract the last digit of the input number using modulo operation
2. Check for potential overflow before appending the digit
3. Append the digit to the result and remove it from the input number

## Complexity Analysis

| Complexity | Analysis |
|------------|----------|
| **Time:** | O(log|x|) — because we process each digit of the input number once |
| **Space:** | O(1) — because we use a constant amount of space to store the result and temporary variables |

## Edge Cases Handled

- Negative numbers
- Numbers with trailing zeros
- Overflow cases

## What I Learned

How to handle overflow when reversing integers without using 64-bit integers

## Similar Problems

- Reverse Linked List
- Palindrome Number

## Solution Code

```text
class Solution {
public:
    int reverse(int x) {
        int ans =0;
        while(x!=0){
            int digit =x%10;
            if(ans>INT_MAX/10||ans<INT_MIN/10){
                return 0;
            }
            ans=(ans*10)+digit;
            x=x/10;
        }
        return ans;
    }
};
```
