# Jump Game IV

**Date:** 2026-05-18  
**Difficulty:** 🔴 **Hard**  
**Tags:** `Array` `Hash Table` `Breadth-First Search`

## Problem Description

Given an array of integers arr , you are initially positioned at the first index of the array. In one step you can jump from index i to index: i + 1 where: i + 1 < arr.length . i - 1 where: i - 1 >= 0 . j where: arr[i] == arr[j] and i != j . Return the minimum number of steps to reach the last index of the array. Notice that you can not jump outside of the array at any time. Example 1: Input: arr = [100,-23,-23,404,100,23,23,23,3,404] Output: 3 Explanation: You need three jumps from index 0 --> 4 --> 3 --> 9. Note that index 9 is the last index of the array. Example 2: Input: arr = [7] Output:

[LeetCode Link](https://leetcode.com/problems/jump-game-iv)

## Approach

Breadth-First Search (BFS) with Hash Table

> Use BFS to explore all possible jumps and track visited indices to find the minimum steps to reach the last index

## Solution Logic

1. Create a hash table to store the indices of each value in the array
2. Initialize a queue with the starting index and a visited array to track visited indices
3. Explore all possible options (move forward, move backward, and move to same valued index) and update the queue and visited array accordingly
4. Repeat the exploration process until the last index is reached or the queue is empty

## Complexity Analysis

| Complexity | Analysis |
|------------|----------|
| **Time:** | O(n) — where n is the number of elements in the array, because each element is visited at most twice (once in the queue and once in the hash table) |
| **Space:** | O(n) — where n is the number of elements in the array, because in the worst case, the queue and hash table can store all elements |

## Edge Cases Handled

- array with duplicate values
- array with single element

## What I Learned

Using a hash table to store the indices of each value can efficiently explore all possible jumps in the array

## Similar Problems

- Jump Game
- Jump Game II

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
