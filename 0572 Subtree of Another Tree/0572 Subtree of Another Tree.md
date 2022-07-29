# 0572. Subtree of Another Tree

* Difficulty: easy
* Link: https://leetcode.com/problems/subtree-of-another-tree/
* Topics: DFS-BFS

# Clarification

1. Check the inputs and outputs

# Solution (BFS)

### Thought Process

- traverse the root tree first
- compare the current node with subtree (isSame?)
- Implement
    
    ```python
    # Definition for a binary tree node.
    # class TreeNode:
    #     def __init__(self, val=0, left=None, right=None):
    #         self.val = val
    #         self.left = left
    #         self.right = right
    class Solution:
        def isSubtree(self, root: Optional[TreeNode], subRoot: Optional[TreeNode]) -> bool:
            
            def isSame(node1: Optional[TreeNode], node2: Optional[TreeNode]) -> bool:
                if not node1 and not node2:
                    return True
                if not node1 or not node2:
                    return False
                if node1.val != node2.val:
                    return False
                return isSame(node1.left, node2.left) and isSame(node1.right, node2.right)
            
            # BFS
            q = collections.deque()
            q.append(root)
            while q:
                current = q.pop()
                if isSame(current, subRoot):
                    return True
                if current:
                    q.append(current.left)
                    q.append(current.right)
            
            return False
    ```
    

### Complexity

- Time complexity: O(V)
    - 遍歷兩棵樹的節點
- Space complexity: