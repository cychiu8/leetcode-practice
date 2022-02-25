# 0103. Binary Tree Zigzag Level Order Traversal

* Difficulty: medium
* Link: https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/
* Topics: DFS-BFS

# Clarification

1. Check the inputs and outputs
    - INPUT: Optional[TreeNode]
    - OUTPUT: List[List[int]]

# Naive Solution

### Thought Process

1. BFS
2. record the level, odds (from left to right) / evens (from right to left)
- Implement
    
    ```python
    # Definition for a binary tree node.
    # class TreeNode:
    #     def __init__(self, val=0, left=None, right=None):
    #         self.val = val
    #         self.left = left
    #         self.right = right
    class Solution:
        def zigzagLevelOrder(self, root: Optional[TreeNode]) -> List[List[int]]:
            if not root:
                return []
            
            # initial
            result = []
            q = collections.deque()
            level = 0
            
            # put root into queue
            q.append(root)
            while q:
                lenq = len(q)
                level += 1
                r = collections.deque()
                for i in range(lenq):
                    current = q.popleft()
    
                    if (level % 2) == 1:
                        r.append(current.val)
                    else:
                        r.appendleft(current.val)
                    
                    if current.left:
                        q.append(current.left)
                    if current.right:
                        q.append(current.right)
                result.append(r)
            return result
    ```