# 0112. Path Sum

* Difficulty: easy
* Link: https://leetcode.com/problems/path-sum/submissions/
* Topics: DFS-BFS

# Solution

### Thought Process

- using DFS to find path and substract it
- Implement
    
    ```python
    # Definition for a binary tree node.
    # class TreeNode:
    #     def __init__(self, val=0, left=None, right=None):
    #         self.val = val
    #         self.left = left
    #         self.right = right
    class Solution:
        def hasPathSum(self, root: Optional[TreeNode], targetSum: int) -> bool:
            if not root:
                return False
            if not root.left and not root.right:
                return targetSum == root.val
            return self.hasPathSum(root.left, targetSum - root.val) or self.hasPathSum(root.right, targetSum - root.val)
    ```
    

### Complexity

- Time complexity: O(V+E)
- Space complexity: O(V)