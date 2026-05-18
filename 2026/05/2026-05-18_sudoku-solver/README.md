# Sudoku Solver

**Date:** 2026-05-18  
**Difficulty:** 🔴 **Hard**  
**Tags:** `Array` `Hash Table` `Backtracking` `Matrix`

## Problem Description

Write a program to solve a Sudoku puzzle by filling the empty cells. A sudoku solution must satisfy all of the following rules : Each of the digits 1-9 must occur exactly once in each row. Each of the digits 1-9 must occur exactly once in each column. Each of the digits 1-9 must occur exactly once in each of the 9 3x3 sub-boxes of the grid. The &#39;.&#39; character indicates empty cells. Example 1: Input: board = [[&quot;5&quot;,&quot;3&quot;,&quot;.&quot;,&quot;.&quot;,&quot;7&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;],[&quot;6&quot;,&quot;.&quot;,&quot;.&quot;,&quot;1&qu

[LeetCode Link](https://leetcode.com/problems/sudoku-solver)

## Approach

Unknown

> Analysis unavailable

## Solution Logic

1. Could not analyze solution

## Complexity Analysis

| Complexity | Analysis |
|------------|----------|
| **Time:** | Unknown |
| **Space:** | Unknown |

## Edge Cases Handled

None specified

## What I Learned

AI analysis failed — solution still committed to GitHub

## Similar Problems

None suggested

## Solution Code

```text
class Solution {
public:
bool isValid(vector < vector < char >> & board, int row, int col, char c) {
  for (int i = 0; i < 9; i++) {
    if (board[i][col] == c)
      return false;

    if (board[row][i] == c)
      return false;

    if (board[3 * (row / 3) + i / 3][3 * (col / 3) + i % 3] == c)
      return false;
  }
  return true;
}

bool solveSudoku(vector < vector < char >> & board) {
  for (int i = 0; i < board.size(); i++) {
    for (int j = 0; j < board[0].size(); j++) {
      if (board[i][j] == '.') {
        for (char c = '1'; c <= '9'; c++) {
          if (isValid(board, i, j, c)) {
            board[i][j] = c;

            if (solveSudoku(board))
              return true;
            else
              board[i][j] = '.';
          }
        }

        return false;
      }
    }
  }
  return true;
}
    
};
```
