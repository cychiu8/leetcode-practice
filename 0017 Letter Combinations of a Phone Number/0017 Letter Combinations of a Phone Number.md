# 0017. Letter Combinations of a Phone Number

* Difficulty: medium
* Link: https://leetcode.com/problems/letter-combinations-of-a-phone-number/
* Topics: Backtracking

# Clarification

1. Check the inputs and outputs
    - INPUT: string
    - OUTPUT: List[String]

# Naive Solution

### Thought Process

- 建立數字對應的 map
- Backtracking
    - 停止條件
        - len(substring) == len(inputstring)
    - 非停止條件
        - forloop
            - 對每個letter backtrack
- Implement
    
    ```python
    class Solution:
        def letterCombinations(self, digits: str) -> List[str]:
            digit_map = {
                "2" : "abc",
                "3":"def",
                "4":"ghi",
                "5":"jkl",
                "6":"mno",
                "7":"pqrs",
                "8":"tuv",
                "9":"wxyz"
            }
            if len(digits) == 0:
                return []
            chars = list(digits)
            result = []
            def backtrack(substr, res):
                if len(substr) == len(digits):
                    return result.append(substr)
                for i in range(len(res)):
                    letters = list(digit_map.get(res[i]))
                    for letter in letters:
                        backtrack(substr+letter, res[i+1:])
            
            backtrack("", chars)
            return result
    ```
    

### Complexity

- Time complexity:
- Space complexity: $O(N)$
    - N: len(digits)