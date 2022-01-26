# 0142. Linked List Cycle II

* Difficulty: medium
* Link: https://leetcode.com/problems/linked-list-cycle-ii/
* Topics: Linked-List, Multiple-Pointers

# Clarification

1. Check the inputs and outputs
    - INPUT: Linked List
    - OUTPUT: ListNode
2. Check the main goal
    - find entry point

# Naive Solution

### Thought Process

1. slow, fast pointer to find the meet point
2. two pointer start from meet point and beginning 
3. the meet point is the entry point
- Implement
    
    ```python
    # Definition for singly-linked list.
    # class ListNode:
    #     def __init__(self, x):
    #         self.val = x
    #         self.next = None
    
    class Solution:
        def detectCycle(self, head: Optional[ListNode]) -> Optional[ListNode]:
            # find cycle
            slow = head
            fast = head
            while slow and fast and fast.next:
                slow = slow.next
                fast = fast.next.next
                if slow == fast:
                    break
            
            if slow == None or fast == None or fast.next == None:
                return None
            
            # find meet point
            fast = head
            while slow != fast:
                slow = slow.next
                fast = fast.next
            
            return slow
    ```
    

### Complexity

- Time complexity: $O(n)$
- Space complexity:$O(1)$

# Note

- Related
    
    [0**287. Find the Duplicate Number** ](https://www.notion.so/0287-Find-the-Duplicate-Number-1f3d3e7e0ab74f22b4402128fc8351ba)