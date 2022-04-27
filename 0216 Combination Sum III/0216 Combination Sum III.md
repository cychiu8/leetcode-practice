# 216. Combination Sum III

* Difficulty: medium
* Link: https://leetcode.com/problems/combination-sum-iii/
* Topics: Backtracking

# Clarification

1. Check the inputs and outputs
    - INPUT:
        - k: int
        - n: int (target)
    - OUTPUT:List[List[int]]

# Naive Solution

### Thought Process

- Backtracking
    - 停止條件
        - len(subset) == k and sum(subset) == n ⇒ add to result
        - sum(subset) > n ⇒ return
        - len(subset) > k ⇒ return
    - 非停止條件
        - subset = subset + res[i]
        - res = res[i+1:]
- Implement
    
    ```python
    class Solution(object):
        def combinationSum3(self, k, n):
            """
            :type k: int
            :type n: int
            :rtype: List[List[int]]
            """
            result = []
            candidates = range(1,10)
            def backtracking(subset, res):
                if len(subset) == k and sum(subset) == n:
                    return result.append(subset)
                if len(subset) > k:
                    return
                if sum(subset) > n:
                    return
                for idx, num in enumerate(res):
                    backtracking(subset + [res[idx]], res[idx+1:])
                    
            backtracking([], candidates)
            return result
    ```