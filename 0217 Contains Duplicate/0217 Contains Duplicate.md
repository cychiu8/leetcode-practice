# 0217. Contains Duplicate

- Difficulty: easy
- Link: https://leetcode.com/problems/contains-duplicate/
- Topics: Array-String

# Clarification

1. Check the inputs and outputs
    - INPUT: List[int]
    - OUTPUT: boolean
2. Check the main goal
    - is there any duplicate numbers

# Naive Solution

### Thought Process

1. create a map
2. iterate the elements
    1. if the element in the map ⇒ return true
3. return false
- Implement
    - Runtime: 556 ms, faster than 18.80%
    - Memory Usage: 25.8 MB, less than 46.06%
    
    ```python
    class Solution:
        def containsDuplicate(self, nums: List[int]) -> bool:
            """
            1. create a map
            2. iterate the elements
                - if the element in the map ⇒ return true
            3. return false
            """
            elementDict = {}
            for num in nums:
                if num in elementDict:
                    return True
                elementDict[num] = True
            return False
    ```
    

### Complexity

- Time complexity: $O(n)$
- Space complexity:$O(n)$

### Problems & Improvement

- python 有 set 這個 data structure
    - 直接使用 set 進行長度比較即可

# Improvement

### Thought Process

1. compare the length of the set and original array
- Implement
    
    ```python
    class Solution:
        def containsDuplicate(self, nums: List[int]) -> bool:
            """
            1. compare the length of the set and original array
            """
            if len(set(nums)) != len(nums):
                return True
            else:
                return False
    ```
    

### Complexity

- Time complexity: $O(1)$
- Space complexity:$O(1)$

# Check special cases, check error

- 

# Note

### Set

- [Time Complexity in Python](https://wiki.python.org/moin/TimeComplexity)