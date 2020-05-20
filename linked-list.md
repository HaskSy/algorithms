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

    def mergeTwoLists(self, l1: ListNode, l2: ListNode) -> ListNode:
        merged_list = pointer = ListNode()  # создаем копию указателя, чтобы не потерять начало
        while l1 and l2:
            if l1.val < l2.val:
                pointer.next = l1
                l1 = l1.next
            else:
                pointer.next = l2
                l2 = l2.next
            pointer = pointer.next

        if l1:
            pointer.next = l1
        elif l2:
            pointer.next = l2
        return merged_list.next
        
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

'''

## Sort List

https://leetcode.com/problems/sort-list/

'''python

'''
