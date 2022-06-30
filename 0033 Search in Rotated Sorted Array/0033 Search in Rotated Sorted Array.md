# 0033. Search in Rotated Sorted Array

* Difficulty: medium
* Link: https://leetcode.com/problems/search-in-rotated-sorted-array/
* Topics: Binary-Search
* highlight: 看 middle 在哪一半的 array，target 在左右的哪一邊?

# Clarification

1. Check the inputs and outputs
    - INPUT:
        - List[int] nums
        - int target
    - OUTPUT:
        - int index

# Solution (Binary search)

### Thought Process

- middle 是在左邊的 array 還是右邊的 array?
    - middle > left ⇒ middle 在左邊 array
    - middle < left ⇒ middle 在右邊 array
- 何種情況下要看 middle 左邊、右邊?
- Implement
    
    ```python
    class Solution:
        def search(self, nums: List[int], target: int) -> int:
            left = 0
            right = len(nums) - 1
            while left <= right:
                middle = (left + right) // 2
                if target == nums[middle]:
                    return middle
                
                # left sorted portion
                if nums[middle] >= nums[left]:
                    if target > nums[middle] or target < nums[left]:
                        left = middle + 1
                    else:
                        right = middle - 1
                # right sorted portion
                else:
                    if target < nums[middle] or target > nums[right]:
                        right = middle - 1
                    else:
                        left = middle + 1
            return -1
    ```
    

### Complexity

- Time complexity: O(log n)
- Space complexity:O(1)

### Note

- **[Search in rotated sorted array - Leetcode 33 - Python](https://www.youtube.com/watch?v=U8XENwh8Oy8)**