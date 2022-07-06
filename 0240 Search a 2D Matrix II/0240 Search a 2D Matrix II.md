# 0240. Search a 2D Matrix II

* Difficulty: medium
* Link: https://leetcode.com/problems/search-a-2d-matrix-ii/
* Topics: Binary-Search

# Clarification

1. Check the inputs and outputs
    - INPUT:
        - List[List[int] matrix
        - int target
    - OUTPUT: boolean

# Solution

### Thought Process

- search from left down corner
- Implement
    
    ```python
    class Solution:
        def searchMatrix(self, matrix: List[List[int]], target: int) -> bool:
            # search from left down corner
            i = 0
            j = len(matrix[0]) - 1
            while i < len(matrix) and j >= 0:
                if target == matrix[i][j]:
                    return True
                if target > matrix[i][j]:
                    i += 1
                else:
                    j -= 1
            return False
    ```
    

### Complexity

- Time complexity: O(log n)
- Space complexity: O(1)