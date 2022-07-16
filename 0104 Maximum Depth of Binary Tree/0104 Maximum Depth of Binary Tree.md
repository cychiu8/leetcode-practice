# 0104. Maximum Depth of Binary Tree

* Difficulty: easy
* Link: https://leetcode.com/problems/maximum-depth-of-binary-tree/
* Topics: DFS-BFS

# Clarification

1. Check the inputs and outputs
2. Check the main goal

# Solution (BFS)

### Thought Process

- BFS
- Implement
    
    ```python
    # Definition for a binary tree node.
    # class TreeNode:
    #     def __init__(self, val=0, left=None, right=None):
    #         self.val = val
    #         self.left = left
    #         self.right = right
    import collections
    class Solution:
        def maxDepth(self, root: Optional[TreeNode]) -> int:
            level = 0
            if not root:
                return level
            
            q = collections.deque()
            q.append(root)
            while q:
                length = len(q)
                level += 1
                for i in range(length):
                    current = q.popleft()
                    if current.right:
                        q.append(current.right)
                    if current.left:
                        q.append(current.left)
            return level
    ```
    

### Complexity

- Time complexity: O(V+E)
- Space complexity: O(V)

# Solution (DFS)

### Thought Process

- DFS
- Implement
    
    ```python
    # Definition for a binary tree node.
    # class TreeNode:
    #     def __init__(self, val=0, left=None, right=None):
    #         self.val = val
    #         self.left = left
    #         self.right = right
    import collections
    class Solution:
        def maxDepth(self, root: Optional[TreeNode]) -> int:
    
            def dfs(root):
                if not root:
                    return 0
                return max(1 + dfs(root.right), 1 + dfs(root.left))
            
            return dfs(root)
    ```
    

### Complexity

- Time complexity: O(V+E)
- Space complexity: