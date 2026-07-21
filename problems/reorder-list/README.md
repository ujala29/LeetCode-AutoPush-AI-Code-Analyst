# Reorder List

**Date:** 2026-07-21  
**Difficulty:** 🟡 **Medium**  
**Tags:** `Linked List` `Two Pointers` `Stack` `Recursion`

## Problem Description

You are given the head of a singly linked-list. The list can be represented as: L 0 &rarr; L 1 &rarr; &hellip; &rarr; L n - 1 &rarr; L n Reorder the list to be on the following form: L 0 &rarr; L n &rarr; L 1 &rarr; L n - 1 &rarr; L 2 &rarr; L n - 2 &rarr; &hellip; You may not modify the values in the list&#39;s nodes. Only nodes themselves may be changed. Example 1: Input: head = [1,2,3,4] Output: [1,4,2,3] Example 2: Input: head = [1,2,3,4,5] Output: [1,5,2,4,3] Constraints: The number of nodes in the list is in the range [1, 5 * 10 4 ] . 1 <= Node.val <= 1000

[LeetCode Link](https://leetcode.com/problems/reorder-list)

## Approach

Two Pointers and Linked List Reversal

> Reorder a singly linked list by finding the middle, reversing the second half, and then merging the two halves

## Solution Logic

1. Find the middle of the list
2. Reverse the second half of the list
3. Merge the two halves

## Complexity Analysis

| Complexity | Analysis |
|------------|----------|
| **Time:** | O(n) — where n is the number of nodes in the linked list, as we are traversing the list three times |
| **Space:** | O(1) — as we are only using a constant amount of space to store the pointers and temporary variables |

## Edge Cases Handled

- Empty list
- List with one node
- List with two nodes

## What I Learned

How to efficiently reorder a linked list by utilizing two pointers and reversing the second half of the list

## Similar Problems

- Reverse Linked List
- Rotate List

## Solution Code

```text
class Solution:
    def reorderList(self, head: Optional[ListNode]) -> None:
        fast = head
        slow = head

        # Step 1: Find the middle of the list
        while fast and fast.next:
            fast = fast.next.next
            slow = slow.next

        # Step 2: Reverse the second half of the list
        second = slow.next
        slow.next = None
        node = None

        while second:
            temp = second.next
            second.next = node
            node = second
            second = temp

        # Step 3: Merge the two halves
        first = head
        second = node

        while second:
            temp1, temp2 = first.next, second.next
            first.next, second.next = second, temp1
            first, second = temp1, temp2
```
