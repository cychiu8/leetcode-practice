# 083. Remove Duplicates from Sorted List

* Difficulty: easy
* Link: https://leetcode.com/problems/remove-duplicates-from-sorted-list/
* Topics: Linked-List

# Clarification

1. Check the inputs and outputs
    - INPUT: Linked List
    - OUTPUT: Linked List

# Naive Solution

### Thought Process

1. iterate the linked list
    
    if the next value is the same as current value: current.next = current.next.next
    
- Implement
    
    ```python
    # Definition for singly-linked list.
    # class ListNode:
    #     def __init__(self, val=0, next=None):
    #         self.val = val
    #         self.next = next
    class Solution:
        def deleteDuplicates(self, head: Optional[ListNode]) -> Optional[ListNode]:
            """
            iterate the linked list
                if the next value is the same as current value: current.next = current.next.next
            """
            
            current = head
            while current and current.next:
                if current.val == current.next.val:
                    current.next = current.next.next
                else:
                    current = current.next
            return head
    ```
    

### Complexity

- Time complexity: $O(n)$
- Space complexity: $O(1)$