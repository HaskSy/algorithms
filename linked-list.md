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

    def reverseList(self, head: ListNode) -> ListNode:
        if head is None or head.next is None:
            return head
        prev = None
        while head:
            node = head.next
            head.next = prev
            prev, head = head, node
        self.head = prev
        return prev

'''

## Middle Of The Linked List

https://leetcode.com/problems/middle-of-the-linked-list/

'''python

    def middleNode(self, head: ListNode) -> ListNode:
        end_of_list = middle_of_list = head        # указатель end_of_list проходит два шага за цикл
        while end_of_list and end_of_list.next:    # указатель middle_of_list проходит и шаг за цикл
            end_of_list = end_of_list.next.next
            middle_of_list = middle_of_list.next
        return middle_of_list

'''

## Palindrome Linked List

https://leetcode.com/problems/palindrome-linked-list/

'''python

    def isPalindrome(self, head: ListNode) -> bool:
        xs = []
        while head:
            xs.append(head.val)
            head = head.next
        return xs == xs[::-1]

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

    def removeNthFromEnd(self, head: ListNode, n: int) -> ListNode:
        answer = ListNode()
        answer.next = head
        pointer_head = head
        pointer_answer = answer

        for _ in range(n):
            pointer_head = pointer_head.next

        while pointer_head:                        # указатель к концу цикла дойдет до конца
            pointer_head = pointer_head.next       # дистанция между указателями pointer_head и pointer_answer будет
            pointer_answer = pointer_answer.next   # фиксирована и равна n
        pointer_answer.next = pointer_answer.next.next  # пропускаем удаляемый элемент, и присоеденяем эл-ты после него
        return answer.next

'''

## Linked List Cycle

https://leetcode.com/problems/linked-list-cycle/

'''python

    def hasCycle(self, head: ListNode) -> bool:
        cycle_a = cycle_b = head
        while cycle_a and cycle_a.next:
            cycle_a = cycle_a.next.next  # указатель cycle_a "двигается быстрее" указателя cycle_b
            cycle_b = cycle_b.next       # если есть цикл, то рано или поздно cycle_a "обгонит на целый круг" cycle_b
            if cycle_a == cycle_b:
                return True
        else:
            return False

'''

## Linked List Cycle II

https://leetcode.com/problems/linked-list-cycle-ii/

'''python

    def detectCycle(self, head: ListNode) -> ListNode:
        cycle_a = cycle_b = head
        while cycle_a and cycle_a.next:  # функция hasCycle
            cycle_a = cycle_a.next.next
            cycle_b = cycle_b.next
            if cycle_a == cycle_b:
                break
        else:
            return None

        """
        Рисуя графы с путями, в конце которых циклы, я заметил, что число ребер от начала пути до узла, с которого
        начинается цикл равно числу ребер от указателя cycle_a до того самого узла.
        (В прицнипе, логично, мог догадаться не рисовав)
        Поэтому просто ставим cycle_b в начало, и равномерно их сдвигаем, когда они совпадут, то оба будут
        смотреть на начало цикла.
        """
        cycle_b = head
        while cycle_a is not cycle_b:
            cycle_a = cycle_a.next
            cycle_b = cycle_b.next
        return cycle_b

'''

## Reorder List

https://leetcode.com/problems/reorder-list/

'''python

    def reorderList(self, head: ListNode) -> None:
        if head is None:
            return

        end_of_list = middle_of_list = head
        while end_of_list and end_of_list.next:  # ищем середину списка
            end_of_list = end_of_list.next.next
            middle_of_list = middle_of_list.next

        reversed_last_half = None   # функция reverseList (разворачиваем вторую половину списка)
        while middle_of_list:
            node = middle_of_list.next
            middle_of_list.next = reversed_last_half
            reversed_last_half, middle_of_list = middle_of_list, node

        first_half = head
        while reversed_last_half.next:  # объединяем по очереди элементы, сначала из first_half,
            temp, first_half.next = first_half.next, reversed_last_half  # а потом из reversed_last_half
            first_half, temp = temp, reversed_last_half.next
            reversed_last_half.next = first_half
            reversed_last_half = temp

'''

## Intersection Of Two Linked Lists

https://leetcode.com/problems/intersection-of-two-linked-lists/

'''python

    def getIntersectionNode(self, headA: ListNode, headB: ListNode) -> ListNode:
        """
        Если расстояние от headA и headB до общего узла равны, то все очевидно, указатели двигаются вровень и 
        своевременно найдут нужный узел. Вообщем, алгоритм заканчивает работу за 2, услово говоря, цикла. 
        Пусть m - расстояния от headA до конца пути, а n - расстояние от headB до конца пути. НУО определим, 
        что m < n. Тогда, к тому моменту, как head_a_copy дойдет до конца и перейдет на начало headB, 
        то расстояние, между head_a_copy и head_b_copy будет n - m + 1 (+1, потому как на переход в начало 
        headB, уходит 1 действие, а указатель head_b_copy в этот момент двигается).
        Итак, head_b_copy доходит до конца, расстояние head_a_copy до конца равно m + 1,
        а расстояние от head_b_copy до конца равно 0.
        head_b_copy переходит в headA => расстояние до конца становится равным m. head_a_copy делает шаг, то есть
        расстояние от head_a_copy до конца также равно m. => Свели все к случаю, когда расстояния до общего узла равны.
        """
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
            while end_of_list and end_of_list.next:  # ищем конец первой половины списка (middle_merge),
                middle_merge = middle_of_list        # и начало второй половины списка (middle_of_list)
                end_of_list = end_of_list.next.next
                middle_of_list = middle_of_list.next

            middle_merge.next = None  # обрезаем список (head_list идет только до середины исходного списка)
            left = merge_sort(head_list)
            right = merge_sort(middle_of_list)
            return merge(left, right)

        return merge_sort(head)

'''