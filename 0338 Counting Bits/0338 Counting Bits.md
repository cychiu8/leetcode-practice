# 0338. Counting Bits

* Difficulty: easy
* Link: https://leetcode.com/problems/counting-bits/
* Topics: Bitwise-Manipulation, Dynamic-Programming

# Clarification

1. Check the inputs and outputs
    - INPUT: int
    - OUTPUT: List[int]

# Naive Solution

### Thought Process

1. loop every integer and caculate the bit
- Implement
    
    ```python
    class Solution:
        def countBits(self, n: int) -> List[int]:
            result = []
            for i in range(n + 1):
                result.append(self.count_bit(i))
            return result
        
        def count_bit(self, n: int) -> int:
            if n == 0:
                return 0
            elif n == 1:
                return 1
            elif (n%2 == 0):
                return self.count_bit(n//2)
            else:
                return 1 + self.count_bit(n//2)
    ```
    

### Complexity

- Time complexity: O(n logn)
- Space complexity: O(1)