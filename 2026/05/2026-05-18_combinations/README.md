# Combinations

**Date:** 2026-05-18  
**Difficulty:** 🟡 **Medium**  
**Tags:** `Backtracking`

## Problem Description

Given two integers n and k , return all possible combinations of k numbers chosen from the range [1, n] . You may return the answer in any order . Example 1: Input: n = 4, k = 2 Output: [[1,2],[1,3],[1,4],[2,3],[2,4],[3,4]] Explanation: There are 4 choose 2 = 6 total combinations. Note that combinations are unordered, i.e., [1,2] and [2,1] are considered to be the same combination. Example 2: Input: n = 1, k = 1 Output: [[1]] Explanation: There is 1 choose 1 = 1 total combination. Constraints: 1 <= n <= 20 1 <= k <= n

[LeetCode Link](https://leetcode.com/problems/combinations)

## Approach

Backtracking

> Generate all combinations of k numbers from 1 to n using recursive backtracking

## Solution Logic

1. Start with an empty combination and add numbers from 1 to n
2. Use a recursive function to explore all possible combinations
3. Backtrack by removing the last added number when a combination is complete or when no more numbers can be added

## Complexity Analysis

| Complexity | Analysis |
|------------|----------|
| **Time:** | O(C(n, k)) — where C(n, k) is the number of combinations of n items taken k at a time, because we generate all possible combinations |
| **Space:** | O(k) — for the recursive call stack and the current combination being built |

## Edge Cases Handled

- n = 1, k = 1
- n = 4, k = 2

## What I Learned

How to use backtracking to generate all combinations of k numbers from a range of 1 to n

## Similar Problems

- Permutations
- Subsets

## Solution Code

```text
class Solution {
private:
 void solving(vector<vector<int>>& ans,int n,int k,vector<int>& pr,int id){
    if(pr.size()==k){
        ans.push_back(pr);
        return;
    }for(int i=id;i<=n;i++){
        pr.push_back(i);
        solving(ans,n,k,pr,i+1);
        pr.pop_back();
    }
 }    
public:
    vector<vector<int>> combine(int n, int k) {
      vector<vector<int>> ans;
      vector<int> pr;
      solving(ans,n,k,pr,1);
      return ans;
    }
};
```
