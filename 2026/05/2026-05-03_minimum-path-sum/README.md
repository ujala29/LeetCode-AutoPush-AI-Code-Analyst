# Minimum Path Sum

**Date:** 2026-05-03  
**Difficulty:** 🟡 **Medium**  
**Tags:** `Array` `Dynamic Programming` `Matrix`

## Problem Description

Given a m x n grid filled with non-negative numbers, find a path from top left to bottom right, which minimizes the sum of all numbers along its path. Note: You can only move either down or right at any point in time. Example 1: Input: grid = [[1,3,1],[1,5,1],[4,2,1]] Output: 7 Explanation: Because the path 1 &rarr; 3 &rarr; 1 &rarr; 1 &rarr; 1 minimizes the sum. Example 2: Input: grid = [[1,2,3],[4,5,6]] Output: 12 Constraints: m == grid.length n == grid[i].length 1 <= m, n <= 200 0 <= grid[i][j] <= 200

[LeetCode Link](https://leetcode.com/problems/minimum-path-sum)

## Approach

Space-Optimized Dynamic Programming (1D Rolling Array)

> Use a single 1D DP array to track minimum path sums row by row, reusing space by updating in-place.

## Solution Logic

1. Initialize a 1D dp array of size n with infinity, except dp[0] = 0, to represent minimum costs to reach each column.
2. For each row i, first update dp[0] by accumulating grid[i][0] (only way to reach left column is from above).
3. For each column j > 0, set dp[j] = min(dp[j] (from above), dp[j-1] (from left)) + grid[i][j], effectively choosing the cheaper incoming direction.
4. After processing all rows, dp[n-1] holds the minimum path sum to reach bottom-right corner.

## Complexity Analysis

| Complexity | Analysis |
|------------|----------|
| **Time:** | O(m*n) — every cell in the grid is visited exactly once |
| **Space:** | O(n) — only a single row-length array is maintained instead of the full m×n DP table |

## Edge Cases Handled

- Single row grid — only right moves possible, dp accumulates correctly
- Single column grid — only down moves possible, dp[0] accumulates all values
- 1x1 grid — returns the single cell value directly
- Grid with zeros — handled naturally by the min comparison

## What I Learned

When doing 2D grid DP where transitions only come from top or left, you can compress the 2D table into a 1D array by processing row by row — dp[j] before update represents 'from above' and dp[j-1] after update represents 'from left', so a single pass per row captures both directions correctly.

## Similar Problems

- Unique Paths
- Unique Paths II
- Triangle (Minimum Path Sum)
- Dungeon Game
- Cherry Pickup
- Maximal Square

## Solution Code

```text
class Solution {
public:
    int minPathSum(vector<vector<int>>& grid) {
        int m = grid.size(), n = grid[0].size();
        vector<int> dp(n, 1e9);
        dp[0] = 0;
        for(int i = 0; i < m; i++){
            dp[0] += grid[i][0];
            for(int j = 1; j < n; j++){
                dp[j] = min(dp[j], dp[j-1]) + grid[i][j];
            }
        }
        return dp[n-1];
    }
};
```
