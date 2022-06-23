# 0378. Kth Smallest Element in a Sorted Matrix

* Difficulty: medium
* Link: https://leetcode.com/problems/kth-smallest-element-in-a-sorted-matrix/
* Topics: Binary-Search, Heap

# Clarification

1. Check the inputs and outputs
    - INPUT: matrix[int][int]
    - OUTPUT: int
2. Check the main goal
    - time complexity < $O(n^2)$

# Naive Solution

<aside>
💡 從最簡單的方法開始 easy solution → only speak out

</aside>

### Thought Process

1. 遍歷整個矩陣，找出第 k 小的值 ⇒ $O(n^2)$ 不符合題目要求

# Solution (Binary search)

### Thought Process

1. 定義 (依據 matrix 之特性)
    - lower = matrix[0][0]
    - upper = matrxi[n][n]
- 猜中間值，並算出有多少個數小於該個中間值
    - 個數 < target ⇒ lower = mid + 1
    - 個數 ≥ target ⇒ upper = mid
- 當 lower ≥ upper 時跳出迴圈，並回傳 lower(/upper)都行
- Implement
    
    ```python
    class Solution:
        def kthSmallest(self, matrix: List[List[int]], k: int) -> int:
            lower = matrix[0][0]
            upper = matrix[-1][-1]
            while lower < upper:
                mid = (lower+upper) // 2
                count = self.numberOfElementsLessOrEqualThan(matrix, mid)
                if count < k:
                    lower = mid + 1
                else:
                    upper = mid
            return lower
        
        def numberOfElementsLessOrEqualThan(self, matrix: List[List[int]], target: int) -> int:
            l = len(matrix)
            i = 0
            j = l - 1
            count = 0
            while j >= 0 and i < l:
                if target < matrix[i][j]:
                    j -= 1
                if target >= matrix[i][j]:
                    count += (j+1)
                    i += 1
            return count
    ```
    

### Complexity

- Time complexity: O(log n)
- Space complexity: O(1)

# Solution (Heap)

- tbd

# Note

- ****[K-th Smallest Element in a Sorted Matrix](https://www.tutorialcup.com/interview/matrix/k-th-smallest-element-in-a-sorted-matrix.htm#Using_min_Heap_data_structure)****
- ****[LeetCode 378(Find K Pairs with Smallest Sums) 心得(Medium)](https://medium.com/@ChYuan/leetcode-378-find-k-pairs-with-smallest-sums-%E5%BF%83%E5%BE%97-medium-c2430d02f260)****