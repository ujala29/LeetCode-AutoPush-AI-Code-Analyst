# Rotating the Box

**Date:** 2026-05-06  
**Difficulty:** 🟡 **Medium**  
**Tags:** `Array` `Two Pointers` `Matrix`

## Problem Description

You are given an m x n matrix of characters boxGrid representing a side-view of a box. Each cell of the box is one of the following: A stone &#39;#&#39; A stationary obstacle &#39;*&#39; Empty &#39;.&#39; The box is rotated 90 degrees clockwise , causing some of the stones to fall due to gravity. Each stone falls down until it lands on an obstacle, another stone, or the bottom of the box. Gravity does not affect the obstacles&#39; positions, and the inertia from the box&#39;s rotation does not affect the stones&#39; horizontal positions. It is guaranteed that each stone in boxGrid rests on an 

[LeetCode Link](https://leetcode.com/problems/rotating-the-box)

## Approach

Unknown

> Solution analysis failed

## Solution Logic

1. Analysis could not be completed

## Complexity Analysis

| Complexity | Analysis |
|------------|----------|
| **Time:** | Unknown |
| **Space:** | Unknown |

## Edge Cases Handled

None specified

## What I Learned

Analysis failed - please check your TrueFoundry configuration

## Similar Problems

None suggested

## Solution Code

```text
class Solution {
public:
    vector<vector<char>> rotateTheBox(vector<vector<char>>& boxGrid) {
        int m = boxGrid.size();
        int n = boxGrid[0].size();

        // Step 1: simulate gravity (right side)
        for (int i = 0; i < m; i++) {
            int empty = n - 1;

            for (int j = n - 1; j >= 0; j--) {
                if (boxGrid[i][j] == '*') {
                    empty = j - 1;
                } 
                else if (boxGrid[i][j] == '#') {
                    swap(boxGrid[i][j], boxGrid[i][empty]);
                    empty--;
                }
            }
        }

        // Step 2: rotate matrix
        vector<vector<char>> res(n, vector<char>(m));

        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                res[j][m - 1 - i] = boxGrid[i][j];
            }
        }

        return res;
    }
};
```
