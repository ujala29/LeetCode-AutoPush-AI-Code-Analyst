# Rotate Image

**Date:** 2026-05-05  
**Difficulty:** 🟡 **Medium**  
**Tags:** `Array` `Math` `Matrix`

## Problem Description

You are given an n x n 2D matrix representing an image, rotate the image by 90 degrees (clockwise). You have to rotate the image in-place , which means you have to modify the input 2D matrix directly. DO NOT allocate another 2D matrix and do the rotation. Example 1: Input: matrix = [[1,2,3],[4,5,6],[7,8,9]] Output: [[7,4,1],[8,5,2],[9,6,3]] Example 2: Input: matrix = [[5,1,9,11],[2,4,8,10],[13,3,6,7],[15,14,12,16]] Output: [[15,13,2,5],[14,3,4,1],[12,6,8,9],[16,7,10,11]] Constraints: n == matrix.length == matrix[i].length 1 <= n <= 20 -1000 <= matrix[i][j] <= 1000

[LeetCode Link](https://leetcode.com/problems/rotate-image)

## Approach

Transpose + Reverse (In-Place Matrix Rotation)

> Rotate matrix 90° clockwise by transposing across main diagonal then reversing each row.

## Solution Logic

1. Step 1: Transpose the matrix — swap matrix[i][j] with matrix[j][i] for all j > i, converting rows into columns.
2. Step 2: Reverse each row — mirror every row horizontally using std::reverse, completing the 90° clockwise rotation.
3. Step 3: Result is the original matrix rotated 90° clockwise in-place with no extra space.

## Complexity Analysis

| Complexity | Analysis |
|------------|----------|
| **Time:** | O(n²) — every element is visited once during transpose (n²/2 swaps) and once during row reversal (n²/2 swaps), totaling O(n²). |
| **Space:** | O(1) — all operations are done in-place using only a constant amount of extra memory for swap temporaries. |

## Edge Cases Handled

- 1x1 matrix — transpose and reverse are no-ops, matrix unchanged correctly
- 2x2 matrix — minimal case where the two-step approach still works correctly
- Even vs odd n — algorithm works uniformly for both even and odd sized matrices

## What I Learned

A 90° clockwise rotation can always be decomposed into two simpler in-place operations: transpose (flip over main diagonal) then horizontal flip (reverse rows). This avoids the complexity of a direct 4-way cyclic swap and is easy to remember and implement correctly.

## Similar Problems

- Transpose Matrix
- Spiral Matrix
- Spiral Matrix II
- Flip an Image
- Rotate Array

## Solution Code

```text


class Solution {
public:
    void rotate(std::vector<std::vector<int>>& matrix) {
        int n = matrix.size();

        // Step 1: **Transpose** the matrix
        // Swap elements across the main diagonal
        for (int i = 0; i < n; ++i) {
            for (int j = i + 1; j < n; ++j) {
                std::swap(matrix[i][j], matrix[j][i]);
            }
        }

        // Step 2: **Reverse** each row
        // Use the std::reverse algorithm
        for (int i = 0; i < n; ++i) {
            std::reverse(matrix[i].begin(), matrix[i].end());
        }
    }
};
```
