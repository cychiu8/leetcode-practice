# 0268. Missing Number

- Difficulty: easy
- Link: https://leetcode.com/problems/missing-number/
- Topics: Array-String

# Clarification

1. Check the inputs and outputs
    - INPUT: list[int]
    - OUTPUT: int
2. Check the main goal
    - find the missing value

# Naive Solution

### Thought Process

1. create an set which include all numbers from 0 to n
2. difference the new set from the input set
3. return the different number in the different set
- Implement
    
    ```python
    class Solution:
        def missingNumber(self, nums: List[int]) -> int:
            """
            1. create an set which include all numbers from 0 to n
            2. difference the new set from the input set
            3. return the different number in the different set
            """
            allNum = set(range(0,len(nums) + 1))
            diff = allNum.difference(set(nums))
            return diff.pop()
    ```
    

### Complexity

- Time complexity: $O(n)$
    - Runtime: 231 ms, faster than 23.17%
    
    ![Untitled](./Untitled.png)
    
- Space complexity: $O(n)$
    - Memory Usage: 16.4 MB, less than 5.81%

### Problems & Improvement

- **Follow up:** Could you implement a solution using only `O(1)` extra space complexity and `O(n)` runtime complexity?

# Improvement

### Thought Process

1. calculate the sum for (0... len(nums)+1) (by gauss algortihm)
2. sum the input array
3. return the subtraction of these two number
- Implement
    
    ```python
    class Solution:
        def missingNumber(self, nums: List[int]) -> int:
            """
            1. calculate the sum for (0... len(nums)+1) (by gauss algortihm)
            2. sum the input array
            3. return the subtraction of these two number
            """
            allSum = (len(nums)+1)*len(nums)/2
            return int(allSum) - sum(nums)
    ```
    

### Complexity

- Time complexity: $O(n)$
    
    Runtime: 160 ms, faster than 41.23%
    
    ![Untitled](./Untitled%201.png)
    
- Space complexity: $O(1)$
    
    Memory Usage: 15.4 MB, less than 50.84%
    

# Check special cases, check error

- 

# Note

- [Time Complexity in Python](https://wiki.python.org/moin/TimeComplexity)