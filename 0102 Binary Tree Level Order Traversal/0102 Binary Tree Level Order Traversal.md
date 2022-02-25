# 0102. Binary Tree Level Order Traversal

* Difficulty: medium
* Link: https://leetcode.com/problems/binary-tree-level-order-traversal/
* Topics: DFS-BFS

# Clarification

1. Check the inputs and outputs
    - INPUT: Optional[TreeNode]
    - OUTPUT: List[List[int]

# Naive Solution

### Thought Process

1. BFS
2. get the nodes from level to level
- Implement
    
    ```python
    # Definition for a binary tree node.
    # class TreeNode:
    #     def __init__(self, val=0, left=None, right=None):
    #         self.val = val
    #         self.left = left
    #         self.right = right
    class Solution:
        def levelOrder(self, root: Optional[TreeNode]) -> List[List[int]]:
            
            if not root:
                return []
            
            result = []
            q = collections.deque()
            q.append(root)
            
            while q:
                lenq = len(q)
                r = []
                for i in range(lenq):
                    current = q.popleft()
                    r.append(current.val)
                    if current.left:
                        q.append(current.left)
                    if current.right:
                        q.append(current.right)
                result.append(r)
                
            return result
    ```
    

### Complexity

- Time complexity: $O(N)$
    - 遍歷每個節點一次
- Space complexity: $O(N)$
    - queue 最大為所有 node 個數