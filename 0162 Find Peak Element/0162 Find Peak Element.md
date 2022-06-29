# 0162. Find Peak Element

* Difficulty: medium
* Link: https://leetcode.com/problems/find-peak-element/
* Topics: Binary-Search

# Clarification

1. Check the inputs and outputs
    - INPUT: List[int] nums
    - OUTPUT: int index
2. Check the main goal
    - solve in O(log n)

# Solution (Binary Search)

### Thought Process

- definitions
    - left = 0
    - right = len(nums) -1
- comparison
    - middle = (left + right) // 2
    - middle + 1
- update
    - middle ≥ middle +1
        
        ⇒ at least one peak at left hand side
        
        ⇒ right = middle
        
        ![Untitled](./Untitled.png)
        
    - middle < middle + 1
        
        ⇒ at least one peak at right hand side
        
        ⇒ left = middle + 1
        
        ![Untitled](./Untitled%201.png)
        
- Implement
    
    ```python
    class Solution:
        def findPeakElement(self, nums: List[int]) -> int:
            left = 0
            right = len(nums) - 1
            while left < right:
                mid = (left + right) // 2
                if nums[mid] >= nums[mid + 1]:
                    right = mid
                else:
                    left = mid + 1
            return left
    ```
    

### Complexity

- Time complexity: O(log n)
- Space complexity: O(1)

# Check special cases, check error

<aside>
💡 How you make break with the function

- 確認特別的 input 是否影響結果
- 確認可能已知的 error
- 有考慮到哪些 assumption
</aside>

- m+1 是否會超過邊界
    - 在 while loop 內 m+1 不會超過邊界
    - 因為 m + 1 要超過邊界的情況為 m 在最後一個 index，但只有 left = right = 會後一個 index 的情況，而當 left = right 即跳出 while loop 了