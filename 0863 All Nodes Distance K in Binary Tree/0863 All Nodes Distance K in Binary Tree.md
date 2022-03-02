# 0863. All Nodes Distance K in Binary Tree

* Difficulty: medium
* Link: https://leetcode.com/problems/all-nodes-distance-k-in-binary-tree/
* Topics: DFS-BFS

# Clarification

1. Check the inputs and outputs
    - INPUT: TreeNode, TreeNode, k
    - OUTPUT: List[int]

# Naive Solution

### Thought Process

1. transfer the tree to graph
2. start from the target node from the graph using bfs
3. return the level k
- Implement
    
    ```python
    # Definition for a binary tree node.
    # class TreeNode:
    #     def __init__(self, x):
    #         self.val = x
    #         self.left = None
    #         self.right = None
    
    class Solution:
        def distanceK(self, root: TreeNode, target: TreeNode, k: int) -> List[int]:
            
            if not root:
                return []
            
            #1. transfer the tree to graph
            graph = {}
            q = collections.deque()
            q.append(root)
            
            while q:
                current = q.popleft()
                if not graph.get(current.val):
                    graph[current.val] = []
                if current.left:
                    leftVal = current.left.val
                    graph[current.val].append(leftVal)
                    graph[leftVal] = [current.val]
                    q.append(current.left)
                if current.right:
                    rightVal = current.right.val
                    graph[current.val].append(rightVal)
                    graph[rightVal] = [current.val]
                    q.append(current.right)
            #2. start from the target node from the graph using bfs
            q.append(target.val)
            level = 0
            result = []
            while level <= k:
                if not q:
                    return []
                lenq = len(q)
                result = []
                for i in range(lenq):
                    current = q.popleft()
                    result.append(current)
                    for n in graph.get(current):
                        graph[n].remove(current)
                        q.append(n)
                level += 1
            #3. return the level k
            return result
    ```
    

### Complexity

- Time complexity:O(N)
- Space complexity:O(N)