# Happy Number

**Date:** 2026-07-11  
**Difficulty:** 🟢 **Easy**  
**Tags:** `Hash Table` `Math` `Two Pointers`

## Problem Description

Write an algorithm to determine if a number n is happy. A happy number is a number defined by the following process: Starting with any positive integer, replace the number by the sum of the squares of its digits. Repeat the process until the number equals 1 (where it will stay), or it loops endlessly in a cycle which does not include 1. Those numbers for which this process ends in 1 are happy. Return true if n is a happy number, and false if not . Example 1: Input: n = 19 Output: true Explanation: 1 2 + 9 2 = 82 8 2 + 2 2 = 68 6 2 + 8 2 = 100 1 2 + 0 2 + 0 2 = 1 Example 2: Input: n = 2 Output:

[LeetCode Link](https://leetcode.com/problems/happy-number)

## Approach

Floyd's Tortoise and Hare (Cycle Detection) algorithm

> Determine if a number is happy by detecting cycles using Floyd's algorithm

## Solution Logic

1. Define a helper function to calculate the sum of squares of digits
2. Initialize two pointers (slow and fast) to the input number
3. Iterate until the slow and fast pointers meet, indicating a cycle or happiness

## Complexity Analysis

| Complexity | Analysis |
|------------|----------|
| **Time:** | O(log n) — because the number of digits in n is logarithmic in n, and each iteration reduces the number of digits |
| **Space:** | O(1) — because only a constant amount of space is used to store the slow and fast pointers |

## Edge Cases Handled

- input number is 1
- input number is a single digit
- input number is a multi-digit number that eventually becomes happy

## What I Learned

The Floyd's Tortoise and Hare algorithm can be used to detect cycles in sequences, and this problem demonstrates its application in determining happy numbers

## Similar Problems

- Linked List Cycle
- Detect Cycle in Graph
- Happy Number II

## Solution Code

```text
class Solution:
    def sqr(self, n: int) -> int:
        total = 0
        while n != 0:
            rem = n % 10
            total += rem * rem
            n = n // 10
        return total   

    def isHappy(self, n: int) -> bool:
        slow = n
        fast = n

        while True:
            slow = self.sqr(slow)
            fast = self.sqr(self.sqr(fast))

            if slow == fast:
                break

        return slow == 1
```
