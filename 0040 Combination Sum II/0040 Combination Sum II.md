# 40. Combination Sum II

* Difficulty: medium
* Link: https://leetcode.com/problems/combination-sum-ii/
* Topics: Array-String, Backtracking

# Clarification

1. Check the inputs and outputs
    - INPUT:
        - canditates: List[int]
        - target: int
    - OUTPUT: List[List[int]

# Naive Solution

### Thought Process

- Backtracking
    - 停止條件
        - sum of subset == target : add to result
        - sum of subset > target : return
    - 未達停止條件
        - subset + res[i]
        - res = res[i+1:]
- 注意：當 res[i] == res[i+1] 時跳過，避免重複
- Implement
    
    ```python
    class Solution(object):
        def combinationSum2(self, candidates, target):
            """
            :type candidates: List[int]
            :type target: int
            :rtype: List[List[int]]
            """
            candidates.sort()
            result = []
            def backtracking(subset, res):
                if sum(subset) == target:
                    return result.append(subset)
                if sum(subset) > target:
                    return
                for idx in range(len(res)):
                    if idx > 0 and res[idx] == res[idx-1]:
                        continue
                    backtracking(subset + [res[idx]], res[idx+1:])
                
            backtracking([], candidates)
            return result
    ```