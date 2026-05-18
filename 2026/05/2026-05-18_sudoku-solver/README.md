# Sudoku Solver

**Date:** 2026-05-18  
**Difficulty:** 🔴 **Hard**  
**Tags:** `Array` `Hash Table` `Backtracking` `Matrix`

## Problem Description

Write a program to solve a Sudoku puzzle by filling the empty cells. A sudoku solution must satisfy all of the following rules : Each of the digits 1-9 must occur exactly once in each row. Each of the digits 1-9 must occur exactly once in each column. Each of the digits 1-9 must occur exactly once in each of the 9 3x3 sub-boxes of the grid. The &#39;.&#39; character indicates empty cells. Example 1: Input: board = [[&quot;5&quot;,&quot;3&quot;,&quot;.&quot;,&quot;.&quot;,&quot;7&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;],[&quot;6&quot;,&quot;.&quot;,&quot;.&quot;,&quot;1&qu

[LeetCode Link](https://leetcode.com/problems/sudoku-solver)

## Approach

Backtracking

> Solve Sudoku puzzle using backtracking algorithm to fill empty cells

## Solution Logic

1. Iterate through the board to find empty cells
2. Try numbers 1-9 in each empty cell and check validity
3. Recursively solve the puzzle and backtrack if a solution is not found

## Complexity Analysis

| Complexity | Analysis |
|------------|----------|
| **Time:** | O(9^(n*n)) — where n is the size of the board, representing the maximum number of possible solutions |
| **Space:** | O(n*n) — for the recursive call stack and the board itself |

## Edge Cases Handled

- Empty board
- Invalid input
- No solution exists

## What I Learned

The importance of using backtracking to solve complex problems with multiple possible solutions

## Similar Problems

- N-Queens
- Permutations

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
