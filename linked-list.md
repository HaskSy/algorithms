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

```python

```

## Middle Of The Linked List

https://leetcode.com/problems/middle-of-the-linked-list/

```python

```

## Palindrome Linked List

https://leetcode.com/problems/palindrome-linked-list/

```python

```

## Merge two Sorted Lists

https://leetcode.com/problems/merge-two-sorted-lists/

```python

```

## Remove Nth Node From End Of List

https://leetcode.com/problems/remove-nth-node-from-end-of-list/

```python

```

## Linked List Cycle

https://leetcode.com/problems/linked-list-cycle/

```python

```

## Linked List Cycle II

https://leetcode.com/problems/linked-list-cycle-ii/

```python

```

## Reorder List

https://leetcode.com/problems/reorder-list/

```python

```

## Intersection Of Two Linked Lists

https://leetcode.com/problems/intersection-of-two-linked-lists/

```python

```

## Sort List

https://leetcode.com/problems/sort-list/

```python

    def sortList(self, head: ListNode) -> ListNode:

        def merge(l1: ListNode, l2: ListNode) -> ListNode:
            list_copy = result = ListNode()
            while l1 and l2:
                if l1.val <= l2.val:
                    list_copy.next, l1 = l1, l1.next
                else:
                    list_copy.next, l2 = l2, l2.next
                list_copy = list_copy.next
            if l1:
                list_copy.next = l1
            else:
                list_copy.next = l2
            return result.next

        def merge_sort(head_list: ListNode) -> ListNode:
            if not head_list or not head_list.next:
                return head_list
            end_of_list = middle_of_list = head_list

            middle_merge = None
            while end_of_list and end_of_list.next:  
                middle_merge = middle_of_list        
                end_of_list = end_of_list.next.next
                middle_of_list = middle_of_list.next

            middle_merge.next = None  
            left = merge_sort(head_list)
            right = merge_sort(middle_of_list)
            return merge(left, right)

        return merge_sort(head)

```
