# 0637. Average of Levels in Binary Tree

* Difficulty: easy
* Link: https://leetcode.com/problems/average-of-levels-in-binary-tree/
* Topics: DFS-BFS

# Clarification

1. Check the inputs and outputs
    - INPUT: Binary Tree
    - OUTPUT: List[float]

# Naive Solution

### Thought Process

1. BFS (queue)
- Implement
    
    ```python
    # Definition for a binary tree node.
    # class TreeNode:
    #     def __init__(self, val=0, left=None, right=None):
    #         self.val = val
    #         self.left = left
    #         self.right = right
    import queue
    class Solution:
        def averageOfLevels(self, root: Optional[TreeNode]) -> List[float]:
            q = queue.Queue()
            result = []
            q.put(root)
            while not q.empty():
                qLen = q.qsize()
                ave = 0
                for i in range(qLen):
                    current = q.get()
                    ave += current.val
                    if current.left:
                        q.put(current.left)
                    if current.right:
                        q.put(current.right)
                result.append(ave/qLen)
            return result
    ```
    

### Complexity

- Time complexity:$O(n)$
- Space complexity:$O(n)$

### Problems & Improvement

- 不需要使用 library，可使用一般的 array

# Improvement

### Thought Process

- Implement
    
    ```python
    class Solution:
        def averageOfLevels(self, root: TreeNode) -> List[float]:
            q, ans = [root], []
            while len(q):
                qlen, row = len(q), 0
                for i in range(qlen):
                    curr = q.pop(0)
                    row += curr.val
                    if curr.left: q.append(curr.left)
                    if curr.right: q.append(curr.right)
                ans.append(row/qlen)
            return ans
    ```