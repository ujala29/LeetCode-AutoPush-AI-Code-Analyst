# Rotate List

**Date:** 2026-05-05  
**Difficulty:** 🟡 **Medium**  
**Tags:** `Linked List` `Two Pointers`

## Problem Description

Given the head of a linked list, rotate the list to the right by k places. Example 1: Input: head = [1,2,3,4,5], k = 2 Output: [4,5,1,2,3] Example 2: Input: head = [0,1,2], k = 4 Output: [2,0,1] Constraints: The number of nodes in the list is in the range [0, 500] . -100 <= Node.val <= 100 0 <= k <= 2 * 10 9

[LeetCode Link](https://leetcode.com/problems/rotate-list)

## Approach

Circular Linked List with Pointer Manipulation

> Connect tail to head forming a circle, then break at the new tail position after (len - k) steps.

## Solution Logic

1. Step 1: Traverse the list to find its length and locate the tail node.
2. Step 2: Normalize k by taking k % len to eliminate full rotations; return early if k becomes 0.
3. Step 3: Make the list circular by connecting tail->next = head.
4. Step 4: Advance (len - k) steps from head to find the new tail node.
5. Step 5: Set newHead = newTail->next, then break the circle by setting newTail->next = NULL, and return newHead.

## Complexity Analysis

| Complexity | Analysis |
|------------|----------|
| **Time:** | O(n) — single pass to find length, then at most one more pass to find the new tail |
| **Space:** | O(1) — only a constant number of pointers used, no extra data structures |

## Edge Cases Handled

- empty list (head == NULL)
- single node list
- k == 0 (no rotation needed)
- k >= len (normalized via modulo)
- k exactly equals len (full rotation, returns original)
- two-node list with k == 2 (full rotation)

## What I Learned

Rotating a linked list is elegantly solved by temporarily making it circular — instead of physically moving nodes, you just redefine where the list starts and ends. The key insight is that rotating right by k is equivalent to cutting the list at position (len - k) from the head.

## Similar Problems

- Reverse Nodes in k-Group
- Rotate Array
- Split Linked List in Parts
- Reorder List
- Remove Nth Node From End of List

## Solution Code

```text
class Solution {
public:
    ListNode* rotateRight(ListNode* head, int k) {
        if (!head || !head->next || k == 0) return head;

        // Step 1: find length
        int len = 1;
        ListNode* tail = head;
        while (tail->next) {
            tail = tail->next;
            len++;
        }

        // Step 2: normalize k
        k = k % len;
        if (k == 0) return head;

        // Step 3: make circular
        tail->next = head;

        // Step 4: find new tail (len - k - 1 steps)
        int steps = len - k;
        ListNode* newTail = head;
        while (steps > 1) {
            newTail = newTail->next;
            steps--;
        }

        // Step 5: break the circle
        ListNode* newHead = newTail->next;
        newTail->next = NULL;

        return newHead;
    }
};
```
