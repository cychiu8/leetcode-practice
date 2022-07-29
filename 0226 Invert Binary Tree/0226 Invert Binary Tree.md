# 0226. Invert Binary Tree

* Difficulty: easy
* Link: https://leetcode.com/problems/invert-binary-tree/
* Topics: DFS-BFS

# Clarification

1. Check the inputs and outputs

# Solution

### Thought Process

1. traverse the tree by BFS
2. swap left node and right node
- Implement
    
    ```python
    # Definition for a binary tree node.
    # class TreeNode:
    #     def __init__(self, val=0, left=None, right=None):
    #         self.val = val
    #         self.left = left
    #         self.right = right
    class Solution:
        def invertTree(self, root: Optional[TreeNode]) -> Optional[TreeNode]:
            if not root:
                return root
            
            q = collections.deque()
            q.append(root)
            
            while q:
                current = q.popleft()
                
                if current.left:
                    q.append(current.left)
                if current.right:
                    q.append(current.right)
                
                tmp = current.left
                current.left = current.right
                current.right = tmp
                
            return root
    ```
    

### Complexity

- Time complexity: O(V)
    - V is the number of the tree nodes
- Space complexity: O(V)
    - V is the number of the tree nodes