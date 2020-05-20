# Linked List

+ [Reverse Linked List](#reverse-linked-list)
+ [Middle Of The Linked List](#middle-of-the-linked-list)
+ [Palindrome Linked List](#palindrome-linked-list)
+ [Merge two Sorted Lists](#merge-two-sorted-lists)
+ [Remove Nth Node From End Of List](#remove-nth-node-from-end-of-list)
+ [Linked List Cycle](#linked-list-cycle)
+ [Linked List Cycle II](#linked-list-cycle-ii)
+ [Reorder List](#reorder-list)
+ [Intersection Of Two Linked Lists](#intersection-of-two-linked-lists)
+ [Sort List](#sort-list)

## Reverse Linked List

https://leetcode.com/problems/reverse-linked-list/

'''python

'''

## Middle Of The Linked List

https://leetcode.com/problems/middle-of-the-linked-list/

'''python

'''

## Palindrome Linked List

https://leetcode.com/problems/palindrome-linked-list/

'''python

'''

## Merge two Sorted Lists

https://leetcode.com/problems/merge-two-sorted-lists/

'''python

'''

## Remove Nth Node From End Of List

https://leetcode.com/problems/remove-nth-node-from-end-of-list/

'''python

'''

## Linked List Cycle

https://leetcode.com/problems/linked-list-cycle/

'''python

'''

## Linked List Cycle II

https://leetcode.com/problems/linked-list-cycle-ii/

'''python

'''

## Reorder List

https://leetcode.com/problems/reorder-list/

'''python

'''

## Intersection Of Two Linked Lists

https://leetcode.com/problems/intersection-of-two-linked-lists/

'''python

    def getIntersectionNode(self, headA: ListNode, headB: ListNode) -> ListNode:
        head_a_copy, head_b_copy = headA, headB
        while head_a_copy is not head_b_copy:
            if head_a_copy:
                head_a_copy = head_a_copy.next
            else:
                head_a_copy = headB
            if head_b_copy:
                head_b_copy = head_b_copy.next
            else:
                head_b_copy = headA
        return head_a_copy

'''

## Sort List

https://leetcode.com/problems/sort-list/

'''python

'''
