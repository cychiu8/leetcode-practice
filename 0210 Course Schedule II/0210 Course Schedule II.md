# 0210. Course Schedule II

* Difficulty: medium
* Link: https://leetcode.com/problems/course-schedule-ii/
* Topics: DFS-BFS, Graph

# Clarification

1. Check the inputs and outputs
    - INPUT:List[List[int]]
    - OUTPUT: List[int]

# Naive Solution

### Thought Process

1. establish the graph of the courses
    1. record the pre request course as the successor of the course
    2. record the in degree and out degree of each node
2. start from the node which have minimal predecessor (minimal in degree)
- Implement
    
    ```python
    class Solution:
        def findOrder(self, numCourses: int, prerequisites: List[List[int]]) -> List[int]:
            # create graph
            graph = [[] for i in range(numCourses)]
            indegree = [0] * numCourses
            outdegree = [0] * numCourses
            for course, pre in prerequisites:
                graph[course].append(pre)
                outdegree[course] += 1
                indegree[pre] += 1
            
            # dfs from minimal indegree node
            result = []
            # 0 for unvisited, 1 for visiting, 2 for visited
            course_status = [0] * numCourses
            
            def isDfsCycle(node):
                if course_status[node] == 1:
                    return True
                if course_status[node] == 2:
                    return False
                course_status[node] = 1
                for pre in graph[node]:
                    if isDfsCycle(pre):
                        return True
                course_status[node] = 2
                result.append(node)
                return False
            
            mini_node = indegree.index(min(indegree))
            while indegree[mini_node] != numCourses + 1:
                if isDfsCycle(mini_node):
                    return []
                indegree[mini_node] = numCourses + 1
                mini_node = indegree.index(min(indegree))           
            return result
    ```
    

### Problems & Improvement

- 取 indegree 最小的 Node 多花時間

# Improvement

### Thought Process

1. 不需要從 indegree 最小開始，在 DFS 過程中自然會從 prerequest 最少的印出來
- Implement
    
    ```python
    class Solution:
        def findOrder(self, numCourses: int, prerequisites: List[List[int]]) -> List[int]:
            # 建立 graph, 存取每個 node 的 tail -> head
            self.graph = [[] for i in range(numCourses)]
            self.result = []
            for course, pre in prerequisites:
                self.graph[course].append(pre)
                
            # 0: unVisited, 1: visiting, 2: visited
            self.course_status = [0] * numCourses
                
            # 對每個 node 進行 DFS cycle 偵測
            for i in range(numCourses):
                if self.isDfsCycle(i): 
                    return []
            return self.result
        
        def isDfsCycle(self, node):
            if self.course_status[node] == 1:
                return True
            if self.course_status[node] == 2:
                return False
            
            self.course_status[node] = 1
            for pre in self.graph[node]:
                if self.isDfsCycle(pre): return True
            self.course_status[node] = 2
            self.result.append(node)
            return False
    ```