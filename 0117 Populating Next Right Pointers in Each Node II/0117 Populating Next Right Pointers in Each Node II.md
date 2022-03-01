# 0117. Populating Next Right Pointers in Each Node II

* Difficulty: medium
* Link: https://leetcode.com/problems/populating-next-right-pointers-in-each-node-ii/
* Topics: DFS-BFS
* highlight: 每一次 queue 一開始的長度為同一層 node 的數量

# Clarification

1. Check the inputs and outputs
    - INPUT: Node
    - OUTPUT: Node

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
        def connect(self, root: 'Node') -> 'Node':
            if not root:
                return root
            
            q = collections.deque()
            q.append(root)
            
            while q:
                lenq = len(q)
                prev = Node(None)
                for i in range(lenq):
                    current = q.popleft()
                    if current.left:
                        q.append(current.left)
                    if current.right:
                        q.append(current.right)
                    
                    if prev:
                        prev.next = current
                    prev = current
                prev = None
            return root
    ```
    

### Complexity

- Time complexity: O(N)
- Space complexity: O(N)