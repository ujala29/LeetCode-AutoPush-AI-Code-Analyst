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

1. Step 1: Build a prefix maximum array where preMax[i] = max(nums[0..i]), representing the best value reachable by jumping backwards (since jumping left requires nums[j] > nums[i], the max prefix value is always reachable going left).
2. Step 2: Traverse right to left while maintaining a suffix minimum (sufMin). At each index i, if preMax[i] > sufMin, it means we can jump forward to some index where the value is smaller, and from there we already computed the best answer (ans[i+1] propagates the best reachable value).
3. Step 3: Otherwise, the best reachable value from i is preMax[i] itself (we can only go left to reach higher values, and the prefix max captures that). Update sufMin as we move left.

## Complexity Analysis

| Complexity | Analysis |
|------------|----------|
| **Time:** | O(n) — single pass to build prefix max array, single right-to-left pass for the answer |
| **Space:** | O(n) — prefix max array of size n plus the output array |

## Edge Cases Handled

- All equal elements (no valid jumps possible, each index returns its own value)
- Single element array
- Strictly increasing array (can only jump backwards)
- Strictly decreasing array (can only jump forwards)

## What I Learned

The key insight is that jumping left always leads to a larger value (by rule), so the prefix maximum captures all reachable values going left. Jumping right leads to smaller values, but from those positions you can again jump left to reach higher values — this chain is captured by propagating ans[i+1] when a forward jump is beneficial (i.e., when sufMin < preMax[i] means there's a smaller element ahead that opens up a better leftward jump later).

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
