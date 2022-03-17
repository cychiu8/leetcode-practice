# 0169. Majority Element

* Difficulty: easy
* Link: https://leetcode.com/problems/majority-element/
* Topics: Array-String, Sort

# Clarification

1. Check the inputs and outputs
    - INPUT: List[int]
    - OUTPUT: int

# Naive Solution

### Thought Process

1. loop 一次，用一個 dict 紀錄數量
2. 回傳最多數量者
- Implement
    
    ```python
    class Solution(object):
        def majorityElement(self, nums):
            """
            :type nums: List[int]
            :rtype: int
            """
            count = {}
            for num in nums:
                if not count.get(num):
                    count[num] = 1
                else:
                    count[num] += 1
            return max(count, key=count.get)
    ```
    
    ```python
    class Solution(object):
        def majorityElement(self, nums):
            """
            :type nums: List[int]
            :rtype: int
            """
            count = {}
            maxCount, result = 0, 0
            for num in nums:
                count[num] = 1 + count.get(num, 0)
                if count[num] > maxCount:
                    result = num
                    maxCount = count[num]
            return result
    ```
    

### Complexity

- Time complexity: O(N)
- Space complexity: O(N)

### Problems & Improvement

- **Follow-up:**
 Could you solve the problem in linear time and in `O(1)`
 space?

# Improvement

### Thought Process

- ****Moore's Voting Algoritm****
    - 前提：要是 majority element，要有一半以上的數量
- Implement
    
    ```python
    class Solution(object):
        def majorityElement(self, nums):
            """
            :type nums: List[int]
            :rtype: int
            """
            count = 0
            result = 0
            for num in nums:
                if count == 0:
                    result = num
                if num == result:
                    count += 1
                else:
                    count -= 1
                
            return result
    ```
    

### Complexity

- Time complexity:
- Space complexity: