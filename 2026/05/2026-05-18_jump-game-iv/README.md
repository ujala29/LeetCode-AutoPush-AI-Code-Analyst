# Jump Game IV

**Date:** 2026-05-18  
**Difficulty:** 🔴 **Hard**  
**Tags:** `Array` `Hash Table` `Breadth-First Search`

## Problem Description

Given an array of integers arr , you are initially positioned at the first index of the array. In one step you can jump from index i to index: i + 1 where: i + 1 < arr.length . i - 1 where: i - 1 >= 0 . j where: arr[i] == arr[j] and i != j . Return the minimum number of steps to reach the last index of the array. Notice that you can not jump outside of the array at any time. Example 1: Input: arr = [100,-23,-23,404,100,23,23,23,3,404] Output: 3 Explanation: You need three jumps from index 0 --> 4 --> 3 --> 9. Note that index 9 is the last index of the array. Example 2: Input: arr = [7] Output:

[LeetCode Link](https://leetcode.com/problems/jump-game-iv)

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
    int minJumps(vector<int>& arr) 
    {
        int n = arr.size();
        unordered_map<int, vector<int>>mp;
        for (int i = 0; i < n; i++) mp[arr[i]].push_back(i);
        
        queue<int>q;
        vector<bool>visited(n, false);
        q.push(0);
        int steps = 0;
        while(!q.empty())
        {
            int size = q.size();
            while(size--)
            {
                int currIdx = q.front();
                q.pop();
                if (currIdx == n - 1) return steps;
                //================================================================
                //EXPLORE ALL POSSIBLE OPTIONS
                if (currIdx + 1 < n && !visited[currIdx + 1])  //OPTION-1 (Move Forward)
                {
                    visited[currIdx + 1] = true;
                    q.push(currIdx + 1);
                }
                if (currIdx - 1 >= 0 && !visited[currIdx - 1]) //OPTION-2 (Move Backward)
                {
                    visited[currIdx - 1] = true;
                    q.push(currIdx - 1);
                }
                for (int newIdx : mp[arr[currIdx]])  //OPTION-3 (Move to same valued idx)
                {                                 //newIdx coud be before currIdx or after currIdx
                    if (!visited[newIdx]) 
                    {
                        visited[newIdx] = true;
                        q.push(newIdx);
                    }
                }
                //===================================================================
                mp[arr[currIdx]].clear();    //EXPLAINED BELOW :)
            }
            steps++;
        }
        return -1;
    }
};
```
