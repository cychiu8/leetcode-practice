# 0704. Binary Search

* Difficulty: easy
* Link: https://leetcode.com/problems/binary-search/
* Topics: Binary-Search

# Clarification

1. Check the inputs and outputs
    - INPUT: List[int]
    - OUTPUT: index of list
2. Check the main goal
    - the list is sorted
    - time complexity in O(log n)

# Naive Solution

### Thought Process

- 建立兩個指標
    - left pointer: 陣列開頭的位置、值的下限)
    - right pointer: 陣列結束的位置、值的上限
1. 找中間指標對應的值
    - = target ⇒ return
    - < target ⇒ 調高下限 left pointer ++
    - > target ⇒ 調低上限 right pointer - -
- Implement
    
    ```python
    class Solution:
        def search(self, nums: List[int], target: int) -> int:
            left = 0
            right = len(nums) - 1
            while left <= right:
                mid = int((left + right) / 2)
                if nums[mid] == target:
                    return mid
                if nums[mid] < target:
                    left += 1
                elif nums[mid] > target:
                    right -= 1
            return -1
    ```
    

### Complexity

- Time complexity: O(log n)
- Space complexity: O(1)

# Reference

- ****[初學者學演算法｜從時間複雜度認識常見演算法](https://medium.com/appworks-school/%E5%88%9D%E5%AD%B8%E8%80%85%E5%AD%B8%E6%BC%94%E7%AE%97%E6%B3%95-%E5%BE%9E%E6%99%82%E9%96%93%E8%A4%87%E9%9B%9C%E5%BA%A6%E8%AA%8D%E8%AD%98%E5%B8%B8%E8%A6%8B%E6%BC%94%E7%AE%97%E6%B3%95-%E4%B8%80-b46fece65ba5)****