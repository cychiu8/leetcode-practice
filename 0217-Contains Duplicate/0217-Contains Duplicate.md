# 0217. Contains Duplicate

Difficulty: easy
Link: https://leetcode.com/problems/contains-duplicate/
Topics: Array-String

# Clarification

1. Check the inputs and outputs
    - INPUT: List[int]
    - OUTPUT: boolean
2. Check the main goal
    - is there any duplicate numbers

# Naive Solution

<aside>
💡 從最簡單的方法開始 easy solution → only speak out

</aside>

### Thought Process

1. create a map
2. iterate the elements
    1. if the element in the map ⇒ return true
3. return false
- Implement
    - Runtime: 556 ms, faster than 18.80%
    - Memory Usage: 25.8 MB, less than 46.06%
    
    ```python
    class Solution:
        def containsDuplicate(self, nums: List[int]) -> bool:
            """
            1. create a map
            2. iterate the elements
                - if the element in the map ⇒ return true
            3. return false
            """
            elementDict = {}
            for num in nums:
                if num in elementDict:
                    return True
                elementDict[num] = True
            return False
    ```
    

### Complexity

- Time complexity: $O(n)$
- Space complexity:$O(n)$

### Problems & Improvement

<aside>
💡 解釋該解法的問題、可以往哪個方向改善 (一次改善一個問題)

- 瓶頸點在哪裡
- 哪些部分是不需要的
</aside>

- python 有 set 這個 data structure
    - 直接使用 set 進行長度比較即可

# Improvement

### Thought Process

1. compare the length of the set and original array
- Implement
    
    ```python
    class Solution:
        def containsDuplicate(self, nums: List[int]) -> bool:
            """
            1. compare the length of the set and original array
            """
            if len(set(nums)) != len(nums):
                return True
            else:
                return False
    ```
    

### Complexity

- Time complexity: $O(1)$
- Space complexity:$O(1)$

# Check special cases, check error

<aside>
💡 How you make break with the function

- 確認特別的 input 是否影響結果
- 確認可能已知的 error
- 有考慮到哪些 assumption
</aside>

- 

# Note

<aside>
💡 提出可以再改善的方式 (都可以用口語表達即可)

- 可針對特定語言擁有的 function (快速解決問題的方法)
    - 指出此方法的優點 eg. readable
- 精簡成新的 method
    - 一個 method 一件事情
</aside>

<aside>
💡 相關 Note 紀錄

</aside>

### Set

- [Time Complexity in Python](https://wiki.python.org/moin/TimeComplexity)