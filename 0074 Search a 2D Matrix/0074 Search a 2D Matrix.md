# 0074. Search a 2D Matrix

* Difficulty: medium
* Link: https://leetcode.com/problems/search-a-2d-matrix/
* Topics: https://www.notion.so/Binary-Search-a35f22a087844ae2b1736e1c8baaf125
* highlight: 可以分兩半的位置→左下角 (/右上角)

# Clarification

1. Check the inputs and outputs
    - INPUT:
        - List[List[int]] matrix
        - int target
    - OUTPUT: bool

# Solution

### Thought Process

- 從左下角 (或右上角) 開始搜尋
    - 當 target > 當前值 ⇒ 在當前值的右半部
    - 當 target < 當前值 ⇒ 在當前值的上半部
    
    ![Untitled](./Untitled.png)
    
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