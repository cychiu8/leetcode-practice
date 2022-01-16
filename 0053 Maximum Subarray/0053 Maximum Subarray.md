# 0053. Maximum Subarray

- Difficulty: easy
- Link: https://leetcode.com/problems/maximum-subarray/
- Topics: Array-String

# Clarification

1. Check the inputs and outputs
    - INPUT: List[int]
    - OUTPUT: integer
2. Check the main goal
    - find the contiguous subarray which has the largest sum

# Naive Solution

### Thought Process

- wrong answer: subarray 可能在很中間
    1. iterate all element and sum all the array
    2. two pointer from the beginning and the end
        1. if move to forward make the summation better ⇒ forward pointer ++
        2. if move backward make the summation better ⇒ backward pointer - -
        3. both not better ⇒ return sum
- dynamic programming
    - f() ⇒ 從零到i最大的 subarray 加總
    - f(i) = max(f(i - 1) + n[i] , n[i])
- Implement
    
    ```python
    class Solution(object):
        def maxSubArray(self, nums):
            """
            :type nums: List[int]
            :rtype: int
            """
            """
            - dynamic programming
                - f() ⇒ 從零到i最大的 subarray 加總
                - f(i) = max(f(i - 1) + n[i] , n[i])
            """
            
            if len(nums) == 1:
                return nums[0]
            maxSum = nums[0]
            for i in range(1, len(nums)):
                nums[i] = max(nums[i-1]+nums[i], nums[i])
                if nums[i] > maxSum:
                    maxSum = nums[i]
            return maxSum
    ```
    

### Complexity

- Time complexity: $O(n)$
    
    ![Untitled](./Untitled.png)
    
- Space complexity:$O(n)$

### Problems & Improvement

- 

# Improvement

### Thought Process

1. 
- Implement
    
    ```python
    
    ```
    

### Complexity

- Time complexity:
- Space complexity:

# Check special cases, check error

- 

# Note
