# 0113. Path Sum II


* Difficulty: medium
* Link: https://leetcode.com/problems/path-sum-ii/
* Topics: DFS-BFS

# Clarification

1. Check the inputs and outputs

# Solution

### Thought Process

1. traverse all path by DFS and compare the sum
- Implement
    
    ```python
    # Definition for a binary tree node.
    # class TreeNode:
    #     def __init__(self, val=0, left=None, right=None):
    #         self.val = val
    #         self.left = left
    #         self.right = right
    class Solution:
        def pathSum(self, root: Optional[TreeNode], targetSum: int) -> List[List[int]]:
            result = []
            if not root:
                return result
            
            def dfs(current, path, res):
                path.append(current.val)
                res -= current.val
                if not current.left and not current.right:
                    if res == 0:
                        return result.append(path[:])
                if current.left:
                    dfs(current.left, path[:], res)
                if current.right:
                    dfs(current.right, path[:], res)
                
            dfs(root, [], targetSum)
            return result
    ```
    

### Complexity

- Time complexity:
- Space complexity: