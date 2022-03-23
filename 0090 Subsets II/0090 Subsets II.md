# 0090. Subsets II

* Difficulty: medium
* Link: https://leetcode.com/problems/subsets-ii/
* Topics: Array-String, Backtracking
* highlight: 只有在不 duplicate 的情況加上新的 num

# Clarification

1. Check the inputs and outputs
    - INPUT:List[int]
    - OUTPUT:List[List[int]]

# Naive Solution

<aside>
💡 從最簡單的方法開始 easy solution → only speak out

</aside>

### Thought Process

1. 算出每個 number 的數量
2. 真對每個 subset 加上不同數量的 number
- Implement
    
    ```python
    class Solution:
        def subsetsWithDup(self, nums: List[int]) -> List[List[int]]:
            result = [[]]
            num_map = {}
            for num in nums:
                num_map[num] = num_map.get(num, 0) + 1
            for key, value in num_map.items():
                for idx in range(len(result)):
                    for val in range(1,value + 1):
                        result.append(result[idx] + [key] * val)
            return result
    ```
    

### Complexity

- Time complexity:$O(N+N^3)$
- Space complexity:$O(N)$

### Problems & Improvement

- 有使用額外的 space 去存個數
- time complexity 是否可降到 $O(N^2)$

# Improvement

### Thought Process

1. 將 nums 排序
2. 當數字相同時，只新增於相同數字的 subset
    - 因為如果新增到其他的 subset 就會重複
3.  當數字不同時，則可以對 result 內的所有 subset 加上新的數字
- Implement
    
    ```python
    class Solution:
        def subsetsWithDup(self, nums: List[int]) -> List[List[int]]:
            result = [[]]
            curr = []
            nums.sort()
            for idx, num in enumerate(nums):
                if idx > 0 and nums[idx - 1] == num:
                    curr = [subset + [num] for subset in curr]
                else:
                    curr = [subset + [num] for subset in result]
                result += curr
                    
            return result
    ```
    
    - curr: 還可以再增長的 subset
        - 當數字相同時，curr 就只考慮由前一輪的 curr 加上新的 num
        - 當數字不相同時，curr 就可以為全部的 result 加上新的 num
    
    ```jsx
    Example: [1, 2, 2, 3, 3]
    result: [[]]
    ==== idx: 0 ====
    []
    ----
    [1]
    ==== idx: 1 ====
    []
    [1]
    ----
    [2]
    [1, 2]
    ==== idx: 2 ====
    []
    [1]
    [2]
    [1, 2]
    ----
    [2, 2]
    [1, 2, 2]
    ==== idx: 3 ====
    []
    [1]
    [2]
    [1, 2]
    [2, 2]
    [1, 2, 2]
    ----
    [3]
    [1, 3]
    [2, 3]
    [1, 2, 3]
    [2, 2, 3]
    [1, 2, 2, 3]
    ==== idx: 4 ====
    []
    [1]
    [2]
    [1, 2]
    [2, 2]
    [1, 2, 2]
    ----
    [3]
    [1, 3]
    [2, 3]
    [1, 2, 3]
    [2, 2, 3]
    [1, 2, 2, 3]
    ----
    [3, 3]
    [1, 3, 3]
    [2, 3, 3]
    [1, 2, 3, 3]
    [2, 2, 3, 3]
    [1, 2, 2, 3, 3]
    ```
    

### Complexity

- Time complexity: $O(N^2)$
- Space complexity:$O(1)$