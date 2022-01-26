# 0002. Add Two Numbers

* Difficulty: medium
* Link: https://leetcode.com/problems/add-two-numbers/
* Topics: Linked-List
* 
# Clarification

1. Check the inputs and outputs
    - INPUT: 2 Linked List
    - OUTPUT: Linked List

# Naive Solution

### Thought Process

1. 同時 iterate 兩個 list
2. 兩個 val 相加為 output linked list 的 node value
    1. 相加 ≤ 9 :
        
        sum = 當下的 node value
        
    2. 相加 > 10:
        
        sum - 10 = 當下的 node value
        
        下一個 node value = 1
        
- Implement
    
    ```python
    # Definition for singly-linked list.
    # class ListNode:
    #     def __init__(self, val=0, next=None):
    #         self.val = val
    #         self.next = next
    class Solution:
        def addTwoNumbers(self, l1: Optional[ListNode], l2: Optional[ListNode]) -> Optional[ListNode]:
            """
            traverse two list
            add the current two node value
            if the sum > 9:
                result node value = sum
            else:
                result node value = sum - 10
                result next node vaule += 1
            """
            dummy = ListNode(0, None)
            l3 = dummy
            while l1 and l2:
                # new node
                if l3.next == None:
                    newNode = ListNode(0,None)
                    l3.next = newNode
                l3 = l3.next
                
                # calculate
                sum = l1.val + l2.val + l3.val 
                if sum > 9:
                    l3.val = sum - 10
                    nextNode = ListNode(1, None)
                    l3.next = nextNode
                else:
                    l3.val = sum
                l1 = l1.next
                l2 = l2.next
    
            if l3.next:
                now = l1 or l2
                while now:
                    l3 = l3.next
                    sum = l3.val + now.val
                    if sum > 9:
                        l3.val = sum - 10
                        nextNode = ListNode(1, None)
                        l3.next = nextNode
                    else:
                        l3.val = sum
                        l3.next = now.next
                        break
                    now = now.next
            else:
                l3.next = l1 or l2
                
            return dummy.next
    ```
    

### Complexity

- Time complexity: $O(n)$
- Space complexity:$O(1)$

### Problems & Improvement

- 剩餘的 list 與上半部有相同的動作，再 general 化

# Improvement

### Thought Process

1. 把剩餘的部分一起納入 general 一起看
- Implement
    
    ```python
    # Definition for singly-linked list.
    # class ListNode:
    #     def __init__(self, val=0, next=None):
    #         self.val = val
    #         self.next = next
    class Solution:
        def addTwoNumbers(self, l1: Optional[ListNode], l2: Optional[ListNode]) -> Optional[ListNode]:
            """
            traverse two list
            add the current two node value
            if the sum > 9:
                result node value = sum
            else:
                result node value = sum - 10
                result next node vaule += 1
            """
            dummy = ListNode(0, None)
            l3 = dummy
            while l1 or l2:
                # new node
                if l3.next == None:
                    newNode = ListNode(0,None)
                    l3.next = newNode
                l3 = l3.next
    
                # calculate
                val1 = l1.val if l1 else 0
                val2 = l2.val if l2 else 0
                
                sum = val1 + val2 + l3.val 
                if sum > 9:
                    l3.val = sum - 10
                    nextNode = ListNode(1, None)
                    l3.next = nextNode
                else:
                    l3.val = sum
                    
                if l1:
                    l1 = l1.next
                if l2:
                    l2 = l2.next
                
            return dummy.next
    ```
    

### Complexity

- Time complexity: $O(n)$
- Space complexity:$O(1)$

# Check special cases, check error

- 

# Note