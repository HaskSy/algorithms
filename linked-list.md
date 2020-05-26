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
def reverseList(self, head: ListNode) -> ListNode:
    prev = None
    cur = head
    while cur:
        node = cur.next
        cur.next = prev
        prev, cur = cur, node
    self.cur = prev
    return prev

```

## Middle Of The Linked List

https://leetcode.com/problems/middle-of-the-linked-list/

```python
def middleNode(self, head: ListNode) -> ListNode:
    end_of_list = middle_of_list = head
    while end_of_list and end_of_list.next:
        end_of_list = end_of_list.next.next
        middle_of_list = middle_of_list.next
    return middle_of_list

```

## Palindrome Linked List

https://leetcode.com/problems/palindrome-linked-list/

```python
def isPalindrome(self, head: ListNode) -> bool:
    xs = []
    while head:
        xs.append(head.val)
        head = head.next
    return xs == xs[::-1]

def isPalindrome(self, head: ListNode) -> bool:
    reverse = None
    middle = end = head
    while end and end.next:
        end = end.next.next
        reverse, reverse.next, middle = \
            middle, reverse, middle.next
    if end:
        middle = middle.next
    while reverse and reverse.val == middle.val:
        middle = middle.next
        reverse = reverse.next
    return not reverse

```

## Merge two Sorted Lists

https://leetcode.com/problems/merge-two-sorted-lists/

```python
def mergeTwoLists(self, l1: ListNode, l2: ListNode) -> ListNode:
    merged_list = currentNode = ListNode()
    while l1 and l2:
        if l1.val < l2.val:
            currentNode.next = l1
            l1 = l1.next
        else:
            currentNode.next = l2
            l2 = l2.next
        currentNode = currentNode .next

    if l1:
        currentNode.next = l1
    if l2:
        currentNode.next = l2
    return merged_list.next

```

## Remove Nth Node From End Of List

https://leetcode.com/problems/remove-nth-node-from-end-of-list/

```python
def removeNthFromEnd(self, head: ListNode, n: int) -> ListNode:
    answer = ListNode()
    answer.next = head
    pointer_head = head
    pointer_answer = answer

    for _ in range(n):
        pointer_head = pointer_head.next

    while pointer_head:
        pointer_head = pointer_head.next
        pointer_answer = pointer_answer.next
    pointer_answer.next = pointer_answer.next.next
    return answer.next

```

## Linked List Cycle

https://leetcode.com/problems/linked-list-cycle/

```python
def hasCycle(self, head: ListNode) -> bool:
    fast = slow = head
    while fast and fast.next:
        fast = fast.next.next
        slow = slow.next
        if fast == slow:
            return True
    return False

```

## Linked List Cycle II

https://leetcode.com/problems/linked-list-cycle-ii/

```python
def detectCycle(self, head: ListNode) -> ListNode:
    fast = slow = head
    while fast and fast.next:
        fast = fast.next.next
        slow = slow.next
        if fast == slow:
            slow = head
            while fast is not slow:
                fast = fast.next
                slow = slow.next
            return slow
    return None

```

## Reorder List

https://leetcode.com/problems/reorder-list/

```python
def reorderList(self, head: ListNode) -> None:
    if head is None:
        return

    end_of_list = middle_of_list = head
    while end_of_list and end_of_list.next:
        end_of_list = end_of_list.next.next
        middle_of_list = middle_of_list.next

    reversed_last_half = None
    while middle_of_list:
        node = middle_of_list.next
        middle_of_list.next = reversed_last_half
        reversed_last_half, middle_of_list = middle_of_list, node

    first_half = head
    while reversed_last_half.next:
        temp, first_half.next = first_half.next, reversed_last_half
        first_half, temp = temp, reversed_last_half.next
        reversed_last_half.next = first_half
        reversed_last_half = temp

```

## Intersection Of Two Linked Lists

https://leetcode.com/problems/intersection-of-two-linked-lists/

```python
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
