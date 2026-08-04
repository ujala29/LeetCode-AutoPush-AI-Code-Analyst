# Fruit Into Baskets

**Date:** 2026-08-04  
**Difficulty:** 🟡 **Medium**  
**Tags:** `Array` `Hash Table` `Sliding Window`

## Problem Description

You are visiting a farm that has a single row of fruit trees arranged from left to right. The trees are represented by an integer array fruits where fruits[i] is the type of fruit the i th tree produces. You want to collect as much fruit as possible. However, the owner has some strict rules that you must follow: You only have two baskets, and each basket can only hold a single type of fruit. There is no limit on the amount of fruit each basket can hold. Starting from any tree of your choice, you must pick exactly one fruit from every tree (including the start tree) while moving to the right. T

[LeetCode Link](https://leetcode.com/problems/fruit-into-baskets)

## Approach

Sliding Window

> Use a sliding window to track the maximum number of fruits that can be collected with two baskets

## Solution Logic

1. Initialize a frequency dictionary and two pointers
2. Expand the window to the right by incrementing the frequency of the current fruit
3. Shrink the window from the left when there are more than two types of fruits

## Complexity Analysis

| Complexity | Analysis |
|------------|----------|
| **Time:** | O(n) — where n is the number of fruits, because each fruit is visited at most twice |
| **Space:** | O(1) — because the frequency dictionary can store at most three types of fruits |

## Edge Cases Handled

- Empty input array
- Array with a single type of fruit

## What I Learned

The sliding window technique can be used to solve problems that involve finding a maximum or minimum value within a certain range

## Similar Problems

- Longest Substring Without Repeating Characters
- Minimum Window Substring

## Solution Code

```text
from typing import List

class Solution:
    def totalFruit(self, fruits: List[int]) -> int:
        freq = {}
        i = 0
        maxcount = 0

        for j in range(len(fruits)):
            freq[fruits[j]] = freq.get(fruits[j], 0) + 1

            while len(freq) > 2:
                freq[fruits[i]] -= 1
                if freq[fruits[i]] == 0:
                    del freq[fruits[i]]
                i += 1

            maxcount = max(maxcount, j - i + 1)

        return maxcount
```
