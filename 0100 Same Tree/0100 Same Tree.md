# 0100. Same Tree

* Difficulty: easy
* Link: https://leetcode.com/problems/same-tree/
* Topics: DFS-BFS

# Clarification

1. Check the inputs and outputs
    - INPUT:
        - Optional[TreeNode]
        - Optional[TreeNode]
    - OUTPUT:
        - boolean

# Solution

### Thought Process

1. 
- Implement
    
    ```python
    # Definition for a binary tree node.
    # class TreeNode:
    #     def __init__(self, val=0, left=None, right=None):
    #         self.val = val
    #         self.left = left
    #         self.right = right
    class Solution:
        def isSameTree(self, p: Optional[TreeNode], q: Optional[TreeNode]) -> bool:
            def isSame(p,q):
                if not p and not q:
                    return True
                if not p or not q:
                    return False
                if p.val != q.val:
                    return False
                return True
            
            deq_p = collections.deque()
            deq_q = collections.deque()
            
            deq_p.append(p)
            deq_q.append(q)
            
            while deq_p and deq_q:
                p = deq_p.popleft()
                q = deq_q.popleft()
                
                if not isSame(p, q):
                    return False
                
                if p or q:
                    deq_p.append(p.left)
                    deq_p.append(p.right)
                    deq_q.append(q.left)
                    deq_q.append(q.right)
        
            return True
    ```
    

### Complexity

- Time complexity: O(n)
- Space complexity: O(n)
    - to keep a queue