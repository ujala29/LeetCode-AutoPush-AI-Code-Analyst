# Flipping an Image

**Date:** 2026-07-18  
**Difficulty:** 🟢 **Easy**  
**Tags:** `Array` `Two Pointers` `Bit Manipulation` `Matrix` `Simulation`

## Problem Description

Given an n x n binary matrix image , flip the image horizontally , then invert it, and return the resulting image . To flip an image horizontally means that each row of the image is reversed. For example, flipping [1,1,0] horizontally results in [0,1,1] . To invert an image means that each 0 is replaced by 1 , and each 1 is replaced by 0 . For example, inverting [0,1,1] results in [1,0,0] . Example 1: Input: image = [[1,1,0],[1,0,1],[0,0,0]] Output: [[1,0,0],[0,1,0],[1,1,1]] Explanation: First reverse each row: [[0,1,1],[1,0,1],[0,0,0]]. Then, invert the image: [[1,0,0],[0,1,0],[1,1,1]] Exampl

[LeetCode Link](https://leetcode.com/problems/flipping-an-image)

## Approach

Two-Step Iteration

> Flip and invert a binary image horizontally and then invert it

## Solution Logic

1. Reverse each row of the image
2. Invert each element of the image
3. Return the resulting image

## Complexity Analysis

| Complexity | Analysis |
|------------|----------|
| **Time:** | O(n^2) — where n is the number of rows (or columns) in the image, because we are iterating over each element once |
| **Space:** | O(1) — because we are modifying the input image in-place |

## Edge Cases Handled

- Empty image
- Single-element image

## What I Learned

How to efficiently manipulate a binary image by reversing and inverting its elements

## Similar Problems

- Rotating an Image
- Transposing a Matrix

## Solution Code

```text
class Solution:
    def flipAndInvertImage(self, image: List[List[int]]) -> List[List[int]]:
        
        n=len(image)
        for i in range(0,n):
            image[i]=image[i][::-1]
            for j in range(0,n):
                image[i][j]=1 - image[i][j]
                
        return image
                    
```
