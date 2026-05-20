# Trapping Rain Water

**Date:** 2026-05-20  
**Difficulty:** 🔴 **Hard**  
**Tags:** `Array` `Two Pointers` `Dynamic Programming` `Stack` `Monotonic Stack`

## Problem Description

Given n non-negative integers representing an elevation map where the width of each bar is 1 , compute how much water it can trap after raining. Example 1: Input: height = [0,1,0,2,1,0,1,3,2,1,2,1] Output: 6 Explanation: The above elevation map (black section) is represented by array [0,1,0,2,1,0,1,3,2,1,2,1]. In this case, 6 units of rain water (blue section) are being trapped. Example 2: Input: height = [4,2,0,3,2,5] Output: 9 Constraints: n == height.length 1 <= n <= 2 * 10 4 0 <= height[i] <= 10 5

[LeetCode Link](https://leetcode.com/problems/trapping-rain-water)

## Approach

Two Pointers with Dynamic Programming

> Calculate trapped water by finding minimum of left and right max heights for each position

## Solution Logic

1. Compute left max for each position
2. Compute right max for each position
3. Calculate trapped water by finding minimum of left and right max heights for each position

## Complexity Analysis

| Complexity | Analysis |
|------------|----------|
| **Time:** | O(n) — where n is the number of bars in the elevation map, as we make three passes through the array |
| **Space:** | O(n) — where n is the number of bars in the elevation map, as we store left and right max heights for each position |

## Edge Cases Handled

- Empty elevation map
- Elevation map with single bar

## What I Learned

To solve this problem, we need to keep track of the maximum height of the bars to the left and right of each position, and then calculate the trapped water by finding the minimum of these two max heights for each position

## Similar Problems

- Container With Most Water
- Trapping Rain Water II

## Solution Code

```text
class Solution {
public:
    int trap(vector<int>& height) {
        int n = height.size();
        if (n == 0) return 0;

        vector<int> leftmax(n), rightmax(n);
        int water = 0;

        // Compute left max for each position
        leftmax[0] = height[0];
        for (int i = 1; i < n; i++) {
            leftmax[i] = max(leftmax[i - 1], height[i]);
        }

        // Compute right max for each position
        rightmax[n - 1] = height[n - 1];
        for (int i = n - 2; i >= 0; i--) {
            rightmax[i] = max(rightmax[i + 1], height[i]);
        }

        // Calculate trapped water
        for (int i = 0; i < n; i++) {
            water += min(leftmax[i], rightmax[i]) - height[i];
        }

        return water;
    }
};
```
