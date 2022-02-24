# 0107. Binary Tree Level Order Traversal II

Create time: February 24, 2022 6:28 AM
Difficulty: medium
Last edited time: February 24, 2022 8:57 AM
Link: https://leetcode.com/problems/binary-tree-level-order-traversal-ii/
Status: done
Topics: https://www.notion.so/DFS-BFS-63e4d835e9484de693886f084344fdf9
highlight: 視情況記住每層的 level

# Clarification

1. Check the inputs and outputs
    - INPUT: TreeNode
    - OUTPUT: List[List[int]]

# Naive Solution

### Thought Process

1. BFS
2. 將node往前append
- Implement
    
    ```python
    # Definition for a binary tree node.
    # class TreeNode:
    #     def __init__(self, val=0, left=None, right=None):
    #         self.val = val
    #         self.left = left
    #         self.right = right
    class Solution:
        def levelOrderBottom(self, root: Optional[TreeNode]) -> List[List[int]]:
            if not root:
                return []
            result = collections.deque()
            q = collections.deque()
            q.append(root)
            result.append([root.val])
            while q:
                lenq = len(q)
                r = []
                for i in range(lenq):
                    current = q.popleft()
                    if current.left:
                        r.append(current.left.val)
                        q.append(current.left)
                    if current.right:
                        r.append(current.right.val)
                        q.append(current.right)
                if len(r) > 0:
                    result.appendleft(r)
            return result
    ```
    

### Complexity

- Time complexity: $O(N)$
    - 每個 node 遍歷一次
- Space complexity: $O(N)$
    - queue 最長可能為 N

# Solution (DFS)

### Thought Process

1. DFS 
2. Recursive
- Implement
    
    ```python
    # Definition for a binary tree node.
    # class TreeNode:
    #     def __init__(self, val=0, left=None, right=None):
    #         self.val = val
    #         self.left = left
    #         self.right = right
    class Solution:
        def levelOrderBottom(self, root: Optional[TreeNode]) -> List[List[int]]:
            if not root:
                return []
            result=collections.deque()
            self.dfs(root,result,0)
            return result
        
        def dfs(self, current, result, level):
            if not current:
                return result
            
            level+=1
            
            if len(result) < level:
                result.appendleft([current.val])
            else:
                result[-level].append(current.val)
            
            self.dfs(current.left,result,level)
            self.dfs(current.right,result,level)
    ```
    

### Complexity

- Time complexity:
- Space complexity:

# Check special cases, check error

- 確認以下情況
    - 只有root
    - root為null

# Note