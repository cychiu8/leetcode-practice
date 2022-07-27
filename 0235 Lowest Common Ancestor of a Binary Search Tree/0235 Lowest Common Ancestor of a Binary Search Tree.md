# 0235. Lowest Common Ancestor of a Binary Search Tree

* Difficulty: easy
* Link: https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/
* Topics: DFS-BFS

# Clarification

1. Check the inputs and outputs

# Solution (DFS)

### Thought Process

- binary search tree: left descendants ≤ current node ≤ right descendants
    - if p ≤ current node and q ≤ current node ⇒ LCA in the left tree
    - if p ≥ current node and q ≥ current node ⇒ LCA in the right tree
    - if p ≤ current node and q ≥ current node ⇒ current node is the LCA
- Implement
    
    ```python
    # Definition for a binary tree node.
    # class TreeNode:
    #     def __init__(self, x):
    #         self.val = x
    #         self.left = None
    #         self.right = None
    
    class Solution:
        def lowestCommonAncestor(self, root: 'TreeNode', p: 'TreeNode', q: 'TreeNode') -> 'TreeNode':
            if not root:
                return root
            if p.val < root.val and q.val < root.val:
                return self.lowestCommonAncestor(root.left, p, q)
            if p.val > root.val and q.val > root.val:
                return self.lowestCommonAncestor(root.right, p, q)
            return root
    ```
    

### Complexity

- Time complexity: O(V)
    - V: number of nodes
- Space complexity: O(V)
    - V: number of nodes