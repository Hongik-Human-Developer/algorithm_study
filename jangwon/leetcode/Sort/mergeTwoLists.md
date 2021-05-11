# Sort

## leetcode 148. Sort List

### https://leetcode.com/problems/sort-list/submissions/


```py
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def mergeTwoLists(self, l1: ListNode, l2: ListNode) -> ListNode:
        if l1 and l2:
            if l1.val > l2.val:
                l1, l2 = l2, l1
            l1.next = self.mergeTwoLists(l1.next, l2)
        
        return l1 or l2
    
    def sortList(self, head: ListNode) -> ListNode:
        if not (head and head.next):
            return head
        
        # 런너 기법 활용
        half, slow, fast = None, head, head
        while fast and fast.next:
            half, slow, fast = slow, slow.next, fast.next.next
        half.next = None
        
        # 분할 재귀 호출
        l1 = self.sortList(head)
        l2 = self.sortList(slow)
        
        return self.mergeTwoLists(l1, l2)
```

```py
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def sortList(self, head: ListNode) -> ListNode:
        lst: List = []
        p = head
        
        while p:
            lst.append(p.val)
            p = p.next
            
        lst.sort()
        
        p = head
        for i in range(len(lst)):
            p.val = lst[i]
            p = p.next
        
        return head            
```