# 0001. Two Sum

- Category: Array
- Difficulty: easy
- Link: https://leetcode.com/problems/two-sum/

# Clarification

1. Check the inputs and outputs
    - INPUT:
        - Array[int]
        - integer
    - OUTPUT:
        - Array[int]
2. Check the main goal
    - checkt the sum

# Naive Solution

### Thought Process

1. two for loop to check the sum
- Implement
    
    ```python
    class Solution(object):
        def twoSum(self, nums, target):
            """
            :type nums: List[int]
            :type target: int
            :rtype: List[int]
            """
            for i in range(0, len(nums)):
                for j in range(i+1,len(nums)):
                    if nums[i]+nums[j] == target:
                        return [i,j]
            return []
    ```
    

### Complexity

- Time complexity:
    - $O(n^2)$
    
    ![Untitled](./Untitled.png)
    
- Space complexity:
    - $O(n)$

### Problems & Improvement

- too slow to enumerate the sum

# Improvement

### Thought Process

1. sort the array ( ⚠️ the index would be different )
    1. how could I sort the array and I still remember the index
        
        a map?
        
2. check the two summation from different side of the array
    1. if larger than the target ⇒ backward - 1
    2. if smaller than the targe ⇒ forward + 1
    3. the same ⇒ return the index
- Implement
    
    ```python
    class Solution(object):
        indexDict = {}
        def twoSum(self, nums, target):
            """
            :type nums: List[int]
            :type target: int
            :rtype: List[int]
            """
            self.mapArray(nums)
            nums.sort()
            i = 0
            j = len(nums) - 1
            while i!=j:
                tempSum = nums[i] + nums[j]
                if tempSum > target:
                    j = j-1
                elif tempSum < target:
                    i = i+1
                else:
                    return [self.getIndex(nums[i]),self.getIndex(nums[j])]
            return[]
        
        def mapArray(self, nums):
            for i in range(0, len(nums)):
                if nums[i] in self.indexDict:
                    self.indexDict[nums[i]].append(i)
                else:
                    self.indexDict[nums[i]] = [i]
            return
        
        def getIndex(self, key):
            return self.indexDict.get(key).pop()
    ```
    

### Complexity

- Time complexity:
    - $O(n+nlogn)$
        
        ![Untitled](./Untitled%201.png)
        
- Space complexity:
    - O(n)

# Check special cases, check error

- 

# Note
