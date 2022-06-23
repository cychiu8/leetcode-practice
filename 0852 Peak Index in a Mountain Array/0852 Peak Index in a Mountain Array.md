# 0852. Peak Index in a Mountain Array

* Difficulty: easy
* Link: https://leetcode.com/problems/peak-index-in-a-mountain-array/
* Topics: Binary-Search-Tree

# Clarification

1. Check the inputs and outputs
    - INPUT: List[int]
    - OUTPUT: boolean

# Naive Solution

### Thought Process

1. 左右開始往內看，是否越往內都是越大
- Implement
    
    ```python
    class Solution:
        def peakIndexInMountainArray(self, arr: List[int]) -> int:
            left = 0
            right = len(arr) - 1
            left_h = False
            right_h = False
            while left <= right:
                if arr[left + 1] > arr[left]:
                    left += 1
                else:
                    left_h = True
                if arr[right - 1] > arr[right]:
                    right -= 1
                else:
                    right_h = True
                
                if left_h and right_h:
                    break
            return left
    ```
    

### Complexity

- Time complexity: O(n)
    - 所有 element 遍歷一次
- Space complexity: O(1)
    - 儲存 left, right

### Problems & Improvement

- 使用 binary search 降低時間複雜度

# Improvement

### Thought Process

- 比較：arr[m] 與 arr[m+1]
    
    ![Untitled](/Untitled.png)
    
    - arr[m] < arr[m+1] ⇒ 仍上升
        - peak 在 m+1 ~ R 之間 ⇒ left = m+1
    - arr[m] ≥ arr[m+1] ⇒ 已過峰值
        - peak 在 L ~ m 之間 ⇒ right = m
- 跳出條件： L = R 時 ⇒ 在 peak 上
- Implement
    
    ```python
    class Solution:
        def peakIndexInMountainArray(self, arr: List[int]) -> int:
            left = 0
            right = len(arr) - 1
            while left < right:
                mid = (left + right) // 2
                if arr[mid] < arr[mid + 1]:
                    left = mid + 1
                else:
                    right = mid
            return left
    ```
    

### Complexity

- Time complexity: O(log n)
- Space complexity: O(1)

### Exmaple

![Untitled](/Untitled%201.png)