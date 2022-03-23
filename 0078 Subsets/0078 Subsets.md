# 0078. Subsets

* Difficulty: medium
* Link: <https://leetcode.com/problems/subsets/>
* Topics: Array-String, Backtracking

# Clarification

1. Check the inputs and outputs
    * INPUT: List[int]
    * OUTPUT: List[List[int]]

# Naive Solution

### Thought Process

1. 一個一個決定取或不取
2. 加到 result 前判斷是否存在於 result 了

* Implement

    ```python
    class Solution:
        def subsets(self, nums: List[int]) -> List[List[int]]:
            result = []
            subset = []
            
            def add_subset(subset, idx):
                if subset not in result:
                    result.append(subset)
                if idx == len(nums):
                    return
                add_subset(subset + [nums[idx]], idx + 1)
                add_subset(subset, idx + 1)
            add_subset(subset,0)
            return result
    ```

  * 應該是要在 idx == nums 再 append ，就不會有重複 append 的情況

    ```jsx
    class Solution:
        def subsets(self, nums: List[int]) -> List[List[int]]:
            result = []
            subset = []
            
            def add_subset(subset, idx):   
                if idx == len(nums):
                    result.append(subset)
                    return
                add_subset(subset + [nums[idx]], idx + 1)
                add_subset(subset, idx + 1)
            add_subset(subset,0)
            return result
    ```

### Complexity

* Time complexity: $O(2^N)$
* Space complexity:$O(N)$

### Problems & Improvement

* Time complexity 很高

# Improvement

### Thought Process

1. 之前所有的組合 (沒有選當前數字)，再全部加入目前數字(選當前數字)

```jsx
Example : [1,2,3]
result = [[]]
==== idx = 0 ====
[]
----
[1]
==== idx = 1 ====
[]
[1]
----
[2]
[1,2]
==== idx = 2 ====
[]
[1]
[2]
[1,2]
----
[3]
[1,3]
[2,3]
[1,2,3]
```

* Implement

    ```python
    class Solution:
        def subsets(self, nums: List[int]) -> List[List[int]]:
            result = [[]]
            for num in nums:
                for idx in range(len(result)):
                    result.append(result[idx] + [num])
            return result
    ```

    ```jsx
    class Solution:
        def subsets(self, nums: List[int]) -> List[List[int]]:
            result = [[]]
            for num in nums:
                result+= [subset + [num] for subset in result]
                    
            return result
    ```

### Complexity

* Time complexity: $O(N^2)$
* Space complexity:$O(N)$
