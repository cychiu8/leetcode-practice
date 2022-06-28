# 0153. Find Minimum in Rotated Sorted Array

* Difficulty: medium
* Link: https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/
* Topics: Binary-Search

# Clarification

1. Check the inputs and outputs
    - INPUT: List[int]
    - OUTPUT: int

# Solution (Binary Search)

### Thought Process

- 定義 left, right
    - left = 最左邊
    - right = 最右邊
- 比較對象
    - middle 與 right 比較
        - middle ≤ right
            
            ⇒ rotate 點在 middle 的左邊
            
            ⇒ right = middle
            
        - middle > right
            
            ⇒ rotate 點在 middle 的右邊
            
            ⇒ left = middle + 1
            
- Implement
    
    ```python
    class Solution:
        def findMin(self, nums: List[int]) -> int:
            left = 0
            right = len(nums) - 1
            
            while left < right:
                mid = (left + right) // 2
                if nums[mid] <= nums[right]:
                    right = mid
                else:
                    left = mid + 1
            return nums[left]
    ```
    

### Complexity

- Time complexity: O(log n)
- Space complexity: O(1)

### Note

- **[[LeetCode] 153. Find Minimum in Rotated Sorted Array 寻找旋转有序数组的最小值](https://www.cnblogs.com/grandyang/p/4032934.html)**
- **[LeetCode Binary Search Summary 二分搜索法小结](https://www.cnblogs.com/grandyang/p/6854825.html)**