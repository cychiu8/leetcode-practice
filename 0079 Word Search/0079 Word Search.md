# 0079. Word Search

* Difficulty: medium
* Link: https://leetcode.com/problems/word-search/
* Topics: Array-String, Matrix, Backtracking
* highlight: 暴力解

# Clarification

1. Check the inputs and outputs
    - INPUT:List[List[int]]
    - OUTPUT:boolean

# Naive Solution

### Thought Process

1. 每個 node 去比對
- Implement
    
    ```python
    class Solution:
        def exist(self, board: List[List[str]], word: str) -> bool:
            
            if not board or not board[0] or not word:
                return False
            
            rows = len(board)
            columns = len(board[0])
            lenW = len(word)
            visited = set()
            
            def isValid(row, col):
                return ((0 <= row < rows) and (0 <= col < columns))
            
            def searchWords(r, c, i):
                if word[i] == board[r][c] and i == lenW-1:
                    return True
                
                visited.add((r,c))
                directions = [(-1,0), (0,1), (1,0), (0,-1)]
                for dx, dy in directions:
                    newR, newC = r + dx, c + dy
                    if not isValid(newR, newC) or not board[newR][newC] or (newR,newC) in visited: continue
                    if word[i+1] == board[newR][newC] and searchWords(newR, newC, i+1):
                        return True
                visited.remove((r, c))
                return False
            
            for r in range(rows):
                for c in range(columns):
                    if board[r][c] == word[0] and searchWords(r, c, 0):
                        return True
            return False
    ```
    

### Complexity

- Time complexity:O(N*M) * 4^len(word)
- Space complexity:

### Note

- `r in range(R)` 這個的效能很低，要進行判斷是還是使用 `0 <= r < R`
    - 因為這個而 time Limit exceeded