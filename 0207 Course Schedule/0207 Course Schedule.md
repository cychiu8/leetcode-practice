# 0207. Course Schedule

* Difficulty: medium
* Link: https://leetcode.com/problems/course-schedule/
* Topics: DFS-BFS, Graph
* highlight: 偵測 DFS 的 cycle, 每個 node 紀錄狀態有 unVisited, visiting, visited

# Clarification

1. Check the inputs and outputs
    - INPUT: List[List[int]]
    - OUTPUT: boolean

# Naive Solution (wrong)

### Thought Process

1. 用一個 array 存每個 index (course) 的 pre request (pre course) 為多少
2. 對每個 node (course) 進行 DFS
    1. 可以走到 null 表示可以完成該堂課
    2. 若發生 cycle 則是 false：course 在走過的 set 之中
3. 探索過的 course 放到一個 set 之中
- Implement
    
    ```python
    class Solution:
        def canFinish(self, numCourses: int, prerequisites: List[List[int]]) -> bool:
            precourse = [None] * numCourses
            for course, pre in prerequisites:
                precourse[course] = pre
    
            for i in range(numCourses):
                visited = set()
                visited.add(i)
                pre = precourse[i]
                while pre is not None:
                    if pre in visited:
                        return False
                    visited.add(pre)
                    pre = precourse[pre] 
            return True
    ```
    

### Problems

- prerequest 可能不只一堂
    
    ```python
    3
    [[1,0],[1,2],[0,1]]
    ```
    

# Naive Solution

### Thought Process

1. 建立 graph
    - 使用 forward linked list
2. 從每個 node 出發，看使否形成 cycle
    - 與開始的 node 相同
- Implement
    
    ```python
    class Solution:
        def canFinish(self, numCourses: int, prerequisites: List[List[int]]) -> bool:
            # 建立 graph, 存取每個 node 的 tail -> head
            graph = [[] for i in range(numCourses)]
            for course, pre in prerequisites:
                graph[course].append(pre)
                
            # 對每個 node 進行 BFS
            for i in range(numCourses):
                visited = set()
                q = collections.deque()
                # 直接從該個 node 的下一層開始
                for pre in graph[i]:
                    q.append(pre)
                while q:
                    current = q.popleft()
                    visited.add(current)
                    # 與開始的 node 相同 -> 代表有 cycle
                    if current == i:
                        return False
                    
                    for p in graph[current]:
                        if p not in visited:
                            q.append(p)
            return True
    ```
    

### Complexity

- Time complexity: $O(V+E)$
    - V: number of course (nodes)
    - E: number of prerequest (number of arcs)
- Space complexity:

# Improvement

### Thought Process

1. 建立 graph
    - 使用 forward linked list
2. 從每個 node 出發，看使否形成 cycle <重點，如何偵測 cycle 的方式>
    - 與開始的 node 相同
- Implement
    
    ```python
    class Solution:
        def canFinish(self, numCourses: int, prerequisites: List[List[int]]) -> bool:
            # 建立 graph, 存取每個 node 的 tail -> head
            self.graph = [[] for i in range(numCourses)]
            for course, pre in prerequisites:
                self.graph[course].append(pre)
                
            # 0: unVisited, 1: visiting, 2: visited
            self.course_status = [0] * numCourses
                
            # 對每個 node 進行 DFS cycle 偵測
            for i in range(numCourses):
                if self.isDfsCycle(i): return False
            return True
        
        def isDfsCycle(self, node):
            if self.course_status[node] == 1:
                return True
            if self.course_status[node] == 2:
                return False
            
            self.course_status[node] = 1
            for pre in self.graph[node]:
                if self.isDfsCycle(pre): return True
            self.course_status[node] = 2
            return False
    ```
    

# Note

- **[Course Schedule - Graph Adjacency List - Leetcode 207](https://www.youtube.com/watch?v=EgI5nU9etnU)**