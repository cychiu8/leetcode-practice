# 0075. Sort Colors

* Difficulty: medium
* Link: https://leetcode.com/problems/sort-colors/
* Topics: Array-String

# Clarification

1. Check the inputs and outputs
    - INPUT: List[int]
    - OUTPUT: List[int]
2. Check the main goal
    - sort them in-place
    - You must solve this problem without using the library's sort function.

# Naive Solution

### Thought Process

- two pointer
    - last fix one ( from 0 to len(nums) - 1)
    - swap one ( from last fix + 1 to len(nums) -1 _
- Implement
    
    ```python
    class Solution:
        def sortColors(self, nums: List[int]) -> None:
            """
            Do not return anything, modify nums in-place instead.
            """
            for i in range(len(nums) - 1):
                for j in range(i + 1, len(nums)):
                    if nums[j] < nums[i]:
                        nums[i], nums[j] = nums[j], nums[i]
    ```
    

### Complexity

- Time complexity:$O(n^2)$
- Space complexity:$O(1)$


# Improvement

### Thought Process

1. 
- Implement
    
    ```python
    # count sort    
    def sortColors1(self, nums):
        c0 = c1 = c2 = 0
        for num in nums:
            if num == 0:
                c0 += 1
            elif num == 1:
                c1 += 1
            else:
                c2 += 1
        nums[:c0] = [0] * c0
        nums[c0:c0+c1] = [1] * c1
        nums[c0+c1:] = [2] * c2
    ```
    

### Complexity

- Time complexity:$O(n)$
- Space complexity:$O(1)$