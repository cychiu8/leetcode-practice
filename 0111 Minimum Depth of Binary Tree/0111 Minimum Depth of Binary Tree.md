# 0111. Minimum Depth of Binary Tree

* Difficulty: easy
* Link: https://leetcode.com/problems/minimum-depth-of-binary-tree/
* Topics: DFS-BFS
* highlight: BFS 回傳 level

# Clarification

1. Check the inputs and outputs
    - INPUT: Tree
    - OUTPUT: int

# Naive Solution

### Thought Process

1. BFS
2. 當遇到 left, right 皆為 null 時，回傳當下的 level
- Implement
    
    ```python
    # Definition for a binary tree node.
    # class TreeNode:
    #     def __init__(self, val=0, left=None, right=None):
    #         self.val = val
    #         self.left = left
    #         self.right = right
    class Solution:
        def minDepth(self, root: Optional[TreeNode]) -> int:
            """
            1. BFS
            2. 當遇到 left, right 皆為 null 時，回傳當下的 level
            """
            q = []
            if not root:
                return 0
            
            level = 0
            q.append(root)
            while q:
                qLen = len(q)
                level += 1
                for i in range(qLen):
                    current = q.pop(0)
                    if current.left:
                        q.append(current.left)
                    if current.right:
                        q.append(current.right)
                    if not current.left and not current.right:
                        return level
            return level
    ```
    

### Problems & Improvement

- 嘗試使用 DFS, Recursion 的方式

# Improvement

### Thought Process

1. if root = None : return 0
2. 有 root.left 與 root.right 時，取兩者較小的 + 1 (加上自己 root 這層)
3. 只有 root.left 或 root.right 時，取有的那邊往下走
- Implement
    
    ```python
    # Definition for a binary tree node.
    # class TreeNode:
    #     def __init__(self, val=0, left=None, right=None):
    #         self.val = val
    #         self.left = left
    #         self.right = right
    class Solution:
        def minDepth(self, root: Optional[TreeNode]) -> int:
            """
            DFS, recursion
            """
            if not root:
                return 0
            
            if not root.left or not root.right:
                return max(self.minDepth(root.left), self.minDepth(root.right)) + 1
            else:
                return min(self.minDepth(root.left), self.minDepth(root.right)) + 1
    ```