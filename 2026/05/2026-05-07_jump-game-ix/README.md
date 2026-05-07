# Jump Game IX

**Date:** 2026-05-07  
**Difficulty:** 🟡 **Medium**  
**Tags:** `Array` `Dynamic Programming`

## Problem Description

You are given an integer array nums . From any index i , you can jump to another index j under the following rules: Jump to index j where j > i is allowed only if nums[j] < nums[i] . Jump to index j where j < i is allowed only if nums[j] > nums[i] . For each index i , find the maximum value in nums that can be reached by following any sequence of valid jumps starting at i . Return an array ans where ans[i] is the maximum value reachable starting from index i . Example 1: Input: nums = [2,1,3] Output: [2,2,3] Explanation: For i = 0 : No jump increases the value. For i = 1 : Jump to j = 0 as num

[LeetCode Link](https://leetcode.com/problems/jump-game-ix)

## Approach

Prefix Maximum + Suffix Minimum with Right-to-Left DP

> Use prefix max and suffix min arrays to determine reachable maximum values via valid jumps in a single right-to-left pass.

## Solution Logic

1. Step 1: Build a prefix maximum array where preMax[i] = max(nums[0..i]), representing the best value reachable by jumping backwards (since backward jumps require nums[j] > nums[i], the max prefix value is always reachable going left).
2. Step 2: Traverse right to left while maintaining a running suffix minimum (sufMin). At each index i, if preMax[i] > sufMin, it means we can jump forward to some index where the value is smaller, and from there we already know the best answer (ans[i+1] propagates the best reachable value forward).
3. Step 3: If preMax[i] <= sufMin, no beneficial forward jump exists, so the best reachable value is preMax[i] (the best we can get by jumping left or staying). Update sufMin with nums[i] after processing.

## Complexity Analysis

| Complexity | Analysis |
|------------|----------|
| **Time:** | O(n) — single pass to build prefix max array and single right-to-left pass for the answer |
| **Space:** | O(n) — prefix max array and answer array both of size n |

## Edge Cases Handled

- All equal elements (no valid jumps possible, each element returns itself)
- Single element array (trivially returns the element)
- Strictly increasing array (can only jump backwards, prefix max handles it)
- Strictly decreasing array (can only jump forwards, suffix min propagation handles it)

## What I Learned

The key insight is that backward jumps (to smaller indices) always allow reaching the prefix maximum up to that point, while forward jumps (to larger indices) are only beneficial when a smaller value ahead leads to a better overall reachable maximum — this asymmetry lets you solve the problem greedily in one right-to-left sweep.

## Similar Problems

- Jump Game
- Jump Game II
- Jump Game VII
- Next Greater Element
- Stock Span Problem

## Solution Code

```text
class Solution {
public:
    vector<int> maxValue(vector<int>& nums) {
        int n = nums.size();

        vector<int> ans(n);
        vector<int> preMax(n);

        // Prefix maximum
        preMax[0] = nums[0];

        for (int i = 1; i < n; i++) {
            preMax[i] = max(preMax[i - 1], nums[i]);
        }

        int sufMin = INT_MAX;

        // Traverse from right to left
        for (int i = n - 1; i >= 0; i--) {

            if (preMax[i] > sufMin)
                ans[i] = ans[i + 1];
            else
                ans[i] = preMax[i];

            sufMin = min(sufMin, nums[i]);
        }

        return ans;
    }
};
```
