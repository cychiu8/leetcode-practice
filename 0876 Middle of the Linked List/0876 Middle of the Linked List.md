# 0876. Middle of the Linked List

- Difficulty: easy
- Link: https://leetcode.com/problems/middle-of-the-linked-list/
- Topics: Linked-List, Multiple-Pointers

# Clarification

1. Check the inputs and outputs
    - INPUT: LinkedList
    - OUTPUT: ListNode

# Naive Solution

### Thought Process

[Two Pointer]

- concept
    - 指向 middle 的 Pointer 走得比較慢
    - 指向 tail 的 pointer 走得比較快
    
    ![Untitled](./Untitled.png)
    
1. fast = head
2. currentMid = head
3. while fast ≠ null and fast.next ≠ null:
    1. fast += 2, currentMid +=1 
4. return currentMid
- Implement
    
    ```python
    # Definition for singly-linked list.
    # class ListNode:
    #     def __init__(self, val=0, next=None):
    #         self.val = val
    #         self.next = next
    class Solution:
        def middleNode(self, head: Optional[ListNode]) -> Optional[ListNode]:
            """
            fast = head
            currentMid = head
            while fast ≠ null and fast.next ≠ null:
                fast += 2, currentMid +=1 
            return currentMid
            """
            
            fast = head
            mid = head
            while fast != None and fast.next != None:
                mid = mid.next
                fast = fast.next.next
            return mid
    ```
    

### Complexity

- Time complexity:$O(n)$
    
    ![Untitled](./Untitled%201.png)
    
- Space complexity:$O(1)$