---
title: LeetCode21: Merge Two Sorted Lists
layout: single
author_profile: true
read_time: true
comments: true
share: true
related: true
categories:
- PYTHON
toc: true
toc_sticky: true
toc_label: 목차
---

## 문제 
Merge two sorted linked lists and return it as a sorted list. The list should be made by splicing together the nodes of the first two lists.

------


## Example 1:

Input: l1 = [1,2,4], l2 = [1,3,4]
Output: [1,1,2,3,4,4]

## Example 2:

Input: l1 = [], l2 = []
Output: []


## 풀이(1차)
```python
# Definition for singly-linked list.
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next
class Solution:
    def mergeTwoLists(self, l1: Optional[ListNode], l2: Optional[ListNode]) -> Optional[ListNode]:
        root = current = Listnode()
        
        while l1 or l2:
            
            if(l1 and l2):
                if l1.val < l2.val:
                    value = l1.val
                    l1 = l1.next
                else:
                    value = l2.val
                    l2 = l2.next
            elif l1:
                value =l1.val
                l1 = l1.next
            elif l2:
                value = l2.val
                l2 = l2.next
                
            current.next = ListNode(value)
            current = current.next
            
        return root.next

```


## 다른 사람 풀이
```python
# Definition for singly-linked list.
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next
class Solution:
    def mergeTwoLists(self, l1: Optional[ListNode], l2: Optional[ListNode]) -> Optional[ListNode]:
        
        if (not l1) or (l2 and (l1.val > l2.val)):
            l1, l2 = l2, l1
            
        if l1:
            l1.next = self.mergeTwoLists(l1.next, l2)
            
        return l1
```

    