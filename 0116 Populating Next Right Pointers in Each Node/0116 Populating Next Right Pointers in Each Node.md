# 0116. Populating Next Right Pointers in Each Node

* Difficulty: medium
* Link: https://leetcode.com/problems/populating-next-right-pointers-in-each-node/
* Topics: DFS-BFS

# Clarification

1. Check the inputs and outputs
    - INPUT:
    - OUTPUT:

# Naive Solution

### Thought Process

1. BFS
- Implement
    
    ```python
    """
    # Definition for a Node.
    class Node:
        def __init__(self, val: int = 0, left: 'Node' = None, right: 'Node' = None, next: 'Node' = None):
            self.val = val
            self.left = left
            self.right = right
            self.next = next
    """
    
    class Solution:
        def connect(self, root: 'Optional[Node]') -> 'Optional[Node]':
            if not root:
                return root
    
            q = collections.deque()
            q.append(root)
            while q:
                lenQ = len(q)
                for i in range(lenQ):
                    current = q.popleft()
                    if current.left:
                        q.append(current.left)
                    if current.right:
                        q.append(current.right)
                    if i == 0:
                        prev = current
                    else:
                        prev.next = current
                        prev = current
                prev.next = None
            return root
    ```
    

### Complexity

- Time complexity: O(N)
- Space complexity: O(N)