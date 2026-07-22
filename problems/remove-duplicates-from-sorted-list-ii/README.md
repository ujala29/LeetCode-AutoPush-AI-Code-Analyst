# Remove Duplicates from Sorted List II

**Date:** 2026-07-22  
**Difficulty:** 🟡 **Medium**  
**Tags:** `Linked List` `Two Pointers`

## Problem Description

Given the head of a sorted linked list, delete all nodes that have duplicate numbers, leaving only distinct numbers from the original list . Return the linked list sorted as well . Example 1: Input: head = [1,2,3,3,4,4,5] Output: [1,2,5] Example 2: Input: head = [1,1,1,2,3] Output: [2,3] Constraints: The number of nodes in the list is in the range [0, 300] . -100 <= Node.val <= 100 The list is guaranteed to be sorted in ascending order.

[LeetCode Link](https://leetcode.com/problems/remove-duplicates-from-sorted-list-ii)

## Approach

Two Pointers

> Remove duplicates from a sorted linked list by skipping nodes with duplicate values

## Solution Logic

1. Create a dummy node to simplify edge cases
2. Initialize two pointers, ref and cur, to track the current node and its next node
3. Compare the values of cur and cur.next, and skip nodes with duplicate values

## Complexity Analysis

| Complexity | Analysis |
|------------|----------|
| **Time:** | O(n) — where n is the number of nodes in the linked list, because we only traverse the list once |
| **Space:** | O(1) — because we only use a constant amount of space to store the dummy node and the two pointers |

## Edge Cases Handled

- Empty list
- List with single node
- List with all duplicate nodes

## What I Learned

To solve this problem, we need to carefully handle the edge cases and use the two pointers to track the current node and its next node, allowing us to efficiently remove duplicates from the sorted linked list

## Similar Problems

- Remove Duplicates from Sorted List
- Remove Duplicates from Unsorted List

## Solution Code

```text
class Solution:
    def deleteDuplicates(self, head: Optional[ListNode]) -> Optional[ListNode]:
        dummy = ListNode(0, head)
        ref = dummy
        cur = head

        while cur and cur.next:
            if cur.val == cur.next.val:
                while cur.next and cur.val == cur.next.val:
                    cur = cur.next
                ref.next = cur.next
            else:
                ref = ref.next
            cur = cur.next

        return dummy.next
```
