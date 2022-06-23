# 0744. Find Smallest Letter Greater Than Target

* Difficulty: easy
* Link: https://leetcode.com/problems/find-smallest-letter-greater-than-target/
* Topics: Binary-Search

# Clarification

1. Check the inputs and outputs
    - INPUT:
        - List[char]
        - char
    - OUTPUT:char

# Solution

### Thought Process

- binary search
- 一開始直接先判斷超出的部分
- 兩個 pointer
    - left: 指向陣列中最左邊的 char
    - right: 指向陣列中最右邊的 char
- 每次比較 mid = (left+right)/2 index 的 char 與 target
- 若 mid > target → right = mid -1
- 若 mid ≤ target → left = mid + 1
- Implement
    
    ```python
    class Solution:
        def nextGreatestLetter(self, letters: List[str], target: str) -> str:
            # if the number is out of bound
            if target >= letters[-1] or target < letters[0]:
                return letters[0]
            
    				# binary search
            left = 0
            right = len(letters)-1
            while left <= right:
                mid = (left+right)//2
                if  target >= letters[mid]:
                    left = mid+1
                if target < letters[mid]:
                    right = mid-1
                    
            return letters[left]
    ```
    

### Complexity

- Time complexity: log(n)
- Space complexity: log(1)

# Note

- ****[Python easy solution with detail explanation (modified binary search)](https://leetcode.com/problems/find-smallest-letter-greater-than-target/discuss/1568523/Python-easy-solution-with-detail-explanation-(modified-binary-search))****