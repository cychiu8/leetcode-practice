# 0016. 3Sum Closest

* Difficulty: medium
* Link: https://leetcode.com/problems/3sum-closest/
* Topics: Array-String, Multiple-Pointers

# Clarification

1. Check the inputs and outputs
    - INPUT:List[int]
    - OUTPUT: integer

# Naive Solution

### Thought Process

1. sort the array
2. extend two sum
3. keep the closest number
    1. if equals to target : return directly
    2. else: keep the closest number
- Implement
    
    ```python
    class Solution:
        def threeSumClosest(self, nums: List[int], target: int) -> int:
            """
            1. sort the array
            2. extend two sum
            3. keep the closest number
                - if equals to target : return directly
                - else: keep the closest number
            """
            nums.sort()
            closestSum = sys.maxsize
            closestDiff = abs(sys.maxsize-target)
            
            for i in range(0, len(nums) - 2):
                l, r = i + 1, len(nums) - 1
                while l < r:
                    s = nums[i] + nums[l] + nums[r] 
                    diff = s - target
                    if abs(diff) < closestDiff:
                        closestDiff = abs(diff)
                        closest = s
                    if diff > 0:
                        r -= 1
                    elif diff < 0:
                        l += 1
                    else:
                        return target
            
            return closest
    ```
    

### Complexity

- Time complexity:$O(n^2)$
- Space complexity:$O(1)$

### Problems & Improvement

- 不需要額外存 closestDiff

# Improvement

### Thought Process

- Implement
    
    ```python
    class Solution:
        def threeSumClosest(self, nums: List[int], target: int) -> int:
            """
            1. sort the array
            2. extend two sum
            3. keep the closest number
                - if equals to target : return directly
                - else: keep the closest number
            """
            nums.sort()
            closest = nums[0] + nums[1] + nums[2]
            
            for i in range(0, len(nums) - 2):
                l, r = i + 1, len(nums) - 1
                while l < r:
                    s = nums[i] + nums[l] + nums[r] 
                    diff = s - target
                    if abs(s - target) < abs(closest - target):
                        closest = s
                    if s > target:
                        r -= 1
                    elif s < target:
                        l += 1
                    else:
                        return target
            
            return closest
    ```