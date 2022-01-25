# 0203. Remove Linked List Elements

* Difficulty: easy
* Link: https://leetcode.com/problems/remove-linked-list-elements/
* Topics: Linked-List


# Clarification

1. Check the inputs and outputs
    - INPUT: Linked List
    - OUTPUT: Linked List
2. Check the main goal
    - remove the value

# Naive Solution

### Thought Process

1. traverse it and remove the node
- Implement
    
    ```python
    # Definition for singly-linked list.
    # class ListNode:
    #     def __init__(self, val=0, next=None):
    #         self.val = val
    #         self.next = next
    class Solution:
        def removeElements(self, head: Optional[ListNode], val: int) -> Optional[ListNode]:
            """
            traverse it and remove the node
            """
            while head and head.val == val:
                head = head.next
            if not head: return head
            
            current = head.next
            prev = head
            while current:
                while current and current.val == val:
                    prev.next = current.next
                    current = current.next
                if not current:
                    return head
                prev = prev.next
                current = current.next
            return head
    ```
    

### Complexity

- Time complexity:$O(n)$
- Space complexity:$O(1)$

### Problems & Improvement

- current 跟 previous 之間的關係

# Improvement

### Thought Process

- Implement
    
    ```python
    # Definition for singly-linked list.
    # class ListNode:
    #     def __init__(self, val=0, next=None):
    #         self.val = val
    #         self.next = next
    class Solution:
        def removeElements(self, head: Optional[ListNode], val: int) -> Optional[ListNode]:
            """
            traverse it and remove the node
            """
            dummy = ListNode(next = head)
            current = head
            prev = dummy
            while current:
                if current.val == val:
                    prev.next = current.next
                else:
                    prev = current
                current = current.next
            return dummy.next
    ```
    

### Complexity

- Time complexity:$O(n)$
- Space complexity:$O(1)$

# Check special cases, check error

- 

# Note