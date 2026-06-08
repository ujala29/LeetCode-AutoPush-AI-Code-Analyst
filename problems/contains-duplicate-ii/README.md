# Contains Duplicate II

**Date:** 2026-06-08  
**Difficulty:** 🟢 **Easy**  
**Tags:** `Array` `Hash Table` `Sliding Window`

## Problem Description

Given an integer array nums and an integer k , return true if there are two distinct indices i and j in the array such that nums[i] == nums[j] and abs(i - j) <= k . Example 1: Input: nums = [1,2,3,1], k = 3 Output: true Example 2: Input: nums = [1,0,1,1], k = 1 Output: true Example 3: Input: nums = [1,2,3,1,2,3], k = 2 Output: false Constraints: 1 <= nums.length <= 10 5 -10 9 <= nums[i] <= 10 9 0 <= k <= 10 5

[LeetCode Link](https://leetcode.com/problems/contains-duplicate-ii)

## Approach

Sliding Window with Hash Table

> Use a sliding window and hash table to track nearby duplicates in an array

## Solution Logic

1. Initialize a hash table to store elements within the window
2. Expand the window to the right and check for duplicates
3. Shrink the window from the left when it exceeds the given size

## Complexity Analysis

| Complexity | Analysis |
|------------|----------|
| **Time:** | O(n) — where n is the number of elements in the array, because each element is visited at most twice |
| **Space:** | O(min(n, k)) — where k is the window size, because in the worst case, the hash table will store all elements within the window |

## Edge Cases Handled

- Empty array
- Array with a single element
- Window size larger than the array

## What I Learned

Using a sliding window with a hash table can efficiently solve problems involving nearby duplicates or other local constraints

## Similar Problems

- Contains Duplicate
- Subarray with Given Sum

## Solution Code

```text
class Solution {
public:
    bool containsNearbyDuplicate(vector<int>& nums, int k) {
        
        unordered_map<int,int>mp;
       for(int i = 0; i < min((int)nums.size(), k + 1); i++) {
    if(mp.find(nums[i]) != mp.end())
        return true;
    mp[nums[i]]++;
}
        int i=0;
        int j=k+1;
        while(j<nums.size()){
            mp[nums[i]]--;
           if(mp[nums[i]] == 0) mp.erase(nums[i]);
            i++;
            
            if(mp.find(nums[j])!=mp.end()){
                return true;
            }
              mp[nums[j]]++;
              j++;
            
        }
        return false;

    }
};
```
