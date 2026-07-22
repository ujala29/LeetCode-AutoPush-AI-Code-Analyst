# Partition List

**Date:** 2026-07-22  
**Difficulty:** 🟡 **Medium**  
**Tags:** `Linked List` `Two Pointers`

## Problem Description

Given the head of a linked list and a value x , partition it such that all nodes less than x come before nodes greater than or equal to x . You should preserve the original relative order of the nodes in each of the two partitions. Example 1: Input: head = [1,4,3,2,5,2], x = 3 Output: [1,2,2,4,3,5] Example 2: Input: head = [2,1], x = 2 Output: [1,2] Constraints: The number of nodes in the list is in the range [0, 200] . -100 <= Node.val <= 100 -200 <= x <= 200

[LeetCode Link](https://leetcode.com/problems/partition-list)

## Approach

Two Pointers

> Partition linked list around a given value while preserving relative order

## Solution Logic

1. Create two dummy nodes for before and after lists
2. Iterate through the original list and assign nodes to before or after lists based on the given value
3. Connect the before and after lists

## Complexity Analysis

| Complexity | Analysis |
|------------|----------|
| **Time:** | O(n) — where n is the number of nodes in the linked list, as we only traverse the list once |
| **Space:** | O(1) — as we only use a constant amount of space to store the dummy nodes and pointers |

## Edge Cases Handled

- Empty list
- List with single node
- List with all nodes having values less than or greater than the given value

## What I Learned

How to efficiently partition a linked list while preserving the relative order of nodes

## Similar Problems

- Reverse Linked List
- Merge Two Sorted Lists

## Solution Code

```text
class Solution:
    def partition(self, head: Optional[ListNode], x: int) -> Optional[ListNode]:
        before, after = ListNode(0), ListNode(0)
        before_curr, after_curr = before, after
        
        while head:
            if head.val < x:
                before_curr.next, before_curr = head, head
            else:
                after_curr.next, after_curr = head, head
            head = head.next
        
        after_curr.next = None
        before_curr.next = after.next
        
        return before.next
```
