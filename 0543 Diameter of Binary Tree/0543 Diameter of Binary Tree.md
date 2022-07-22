# 0543. Diameter of Binary Tree

* Difficulty: easy
* Link: https://leetcode.com/problems/diameter-of-binary-tree/
* Topics: DFS-BFS

# Clarification

1. Check the inputs and outputs
2. Check the main goal

# Solution

### Thought Process

- 左右子樹的最大深度之和
- Implement
    
    ```python
    # Definition for a binary tree node.
    # class TreeNode:
    #     def __init__(self, val=0, left=None, right=None):
    #         self.val = val
    #         self.left = left
    #         self.right = right
    class Solution:
        
        maxDiameter = 0
        
        def maxDepth(self, root) -> int:
            if not root:
                return 0
    
            leftMax = self.maxDepth(root.left)
            rightMax = self.maxDepth(root.right)
            
            self.maxDiameter = max(self.maxDiameter, leftMax+rightMax)
    
            return 1 + max(leftMax, rightMax)
        
        def diameterOfBinaryTree(self, root: Optional[TreeNode]) -> int:
            self.maxDepth(root)
            return self.maxDiameter
    ```
    

### Complexity

- Time complexity:
- Space complexity: