# 0200. Number of Islands

* Difficulty: medium
* Link: https://leetcode.com/problems/number-of-islands/
* Topics: DFS-BFS
* highlight: 使用 DFS 遍歷相鄰 grid 並使用 set 紀錄 visit

# Clarification

1. Check the inputs and outputs
    - INPUT: List[List[int]]
    - OUTPUT: i
# Solution (DFS recursively)

### Thought Process

1. maintain a visited map
2. start from the first node and go to four direction, if it is not visited mark it
3. search for next island
- Implement
    
    ```python
    class Solution:
        def numIslands(self, grid: List[List[str]]) -> int:
            rows = len(grid)
            columns = len(grid[0])
            visited = [[False] * columns for i in range(rows)]
            directions = [(-1,0), (0,1), (0,-1), (1,0)]
            result = 0
            
            def dfs(row, column):
                visited[row][column] = True
                for dx, dy in directions:
                    newR, newC = row + dx, column + dy
                    if 0 <= newR < rows and 0 <= newC < columns and grid[newR][newC] == "1" and visited[newR][newC] == False:
                        dfs(newR, newC)
            
            for r in range(rows):
                for c in range(columns):
                    if grid[r][c] == "1" and visited[r][c] == False:
                        result += 1
                        dfs(r,c)
            return result
    ```
    

### Complexity

- Time complexity:$O(M*N)$
    - visit each node once
- Space complexity:$O(M*N)$
    - create a visit matrix

### Problems & Improvement

- 範圍的寫法
    
    ```python
    if 0 <= newR < rows:
    可寫成 if newR in range(rows)
    ```
    
- 可以有 BFS / DFS iteratively 的寫法
    - DFS iterative
        
        ```python
        class Solution:
            def numIslands(self, grid: List[List[str]]) -> int:
                rows, columns = len(grid), len(grid[0])
                directions = [(-1,0), (0,1), (0,-1), (1,0)]
                visited = set()
                result = 0
                
                def dfs(row, column):
                    stack = [(row, column)]
                    while stack:
                        (r,c) = stack.pop()
                        visited.add((r,c))
                        for dx, dy in directions:
                            newR, newC = r + dx, c + dy
                            if newR in range(rows) and newC in range(columns) and grid[newR][newC] == "1" and (newR,newC) not in visited:
                                stack.append((newR, newC))
                
                for r in range(rows):
                    for c in range(columns):
                        if grid[r][c] == "1" and (r,c) not in visited:
                            result += 1
                            dfs(r,c)
                return result
        ```
        
    - BFS iterative
        
        ```python
        class Solution:
            def numIslands(self, grid: List[List[str]]) -> int:
                rows, columns = len(grid), len(grid[0])
                directions = [(-1,0), (0,1), (0,-1), (1,0)]
                visited = set()
                result = 0
                
                def bfs(row, column):
                    queue = collections.deque()
                    queue.append((row, column))
                    visited.add((row,column))
                    while queue:
                        r,c = queue.popleft()
                        for dx, dy in directions:
                            newR, newC = r + dx, c + dy
                            if newR in range(rows) and newC in range(columns) and grid[newR][newC] == "1" and (newR,newC) not in visited:
                                visited.add((newR,newC)) #BFS 要先 visted 在加到 queue 當中
                                queue.append((newR, newC))
                
                for r in range(rows):
                    for c in range(columns):
                        if grid[r][c] == "1" and (r,c) not in visited:
                            result += 1
                            bfs(r,c)
                return result
        ```
        

# Note

- ****Complexity of `list` and `collections.deque`**
    - list 使用 pop(0) 為 O(n)，因為要移動所有 element
    - deque 的 popleft() 只要 O(1)
    - ****[Queue, stack, and deque (double-ended queue) in Python](https://note.nkmk.me/en/python-collections-deque/)****