# 0784. Letter Case Permutation

* Difficulty: medium
* Link: https://leetcode.com/problems/letter-case-permutation/
* Topics: Array-String, Backtracking
* highlight: 一個一個加上去

# Clarification

1. Check the inputs and outputs
    - INPUT: string
    - OUTPUT: List[string]

# Naive Solution

<aside>
💡 從最簡單的方法開始 easy solution → only speak out

</aside>

### Thought Process

1. 字母一個一個加上去
- Implement
    
    ```python
    class Solution(object):
        def letterCasePermutation(self, s):
            """
            :type s: str
            :rtype: List[str]
            """
            word = ''
            result = []
            
            def permutation(word, idx):
                if idx == len(s):
                    result.append(word)
                    return
                
                if s[idx].isalpha():
                    permutation(word + s[idx].lower(), idx + 1)
                    permutation(word + s[idx].upper(), idx + 1)
                else:
                    permutation(word + s[idx], idx + 1)
            
            permutation(word, 0)
            return result
    ```
    

### Complexity

- Time complexity: O(len(s))
- Space complexity: O(len(s))