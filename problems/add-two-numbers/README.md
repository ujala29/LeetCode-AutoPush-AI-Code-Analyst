# Add Two Numbers

**Date:** 2026-06-18  
**Difficulty:** 🟡 **Medium**  
**Tags:** `Linked List` `Math` `Recursion`

## Problem Description

You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order , and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list. You may assume the two numbers do not contain any leading zero, except the number 0 itself. Example 1: Input: l1 = [2,4,3], l2 = [5,6,4] Output: [7,0,8] Explanation: 342 + 465 = 807. Example 2: Input: l1 = [0], l2 = [0] Output: [0] Example 3: Input: l1 = [9,9,9,9,9,9,9], l2 = [9,9,9,9] Output: [8,9,9,9,0,0,0,1] Constraints: The number of nodes in each linked list is in 

[LeetCode Link](https://leetcode.com/problems/add-two-numbers)

## Approach

Two-Pointer Technique with Carry

> Add two numbers represented as linked lists with carry propagation

## Solution Logic

1. Initialize a dummy node and a carry variable
2. Iterate through both linked lists, calculating the sum and carry at each step
3. Create new nodes with the calculated sum and update the carry

## Complexity Analysis

| Complexity | Analysis |
|------------|----------|
| **Time:** | O(max(m, n)) — where m and n are the lengths of the input linked lists, because we process each node once |
| **Space:** | O(max(m, n)) — because in the worst case, we might need to create a new linked list with a length equal to the maximum length of the input linked lists plus one |

## Edge Cases Handled

- Input linked lists of different lengths
- Input linked lists with leading zeros

## What I Learned

How to handle carry propagation when adding numbers represented as linked lists

## Similar Problems

- Multiply Strings
- Add Strings

## Solution Code

```text
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        int carry=0;
         ListNode* dummy=new  ListNode(0);
          ListNode* ans=dummy;

        while(l1||l2){
            int val1=l1?l1->val:0;
            int val2=l2?l2->val:0;
            int sum=val1+val2+carry;
             ListNode* temp=new  ListNode(sum%10);
             ans->next=temp;
             ans=ans->next;
          carry=sum/10;
          if(l1) l1=l1->next;
          if(l2) l2=l2->next;
        }
         while(carry>0){
             ListNode* temp=new  ListNode(carry%10);
              ans->next=temp;
             ans=ans->next;
             carry/=10;
         }
        return dummy->next;
    }
};
```
