# 0013. Roman to Integer

- Category: Map
- Difficulty: easy
- Link: https://leetcode.com/problems/roman-to-integer/

# Clarification

1. Check the inputs and outputs
    - INPUT: string (Roman numeral)
    - OUTPUT: intger
2. Check the main goal
    - mapping the Roman numeral to related integer

# Naive Solution

### Thought Process

1. Create a map to mapping from Roman Symbol to values
    - original part
    - subtraction combination
2. iterate the string and add the values
    - is the next value whether is the subtraction combination
        - add the substraction combination
    - add the original value
3. return
- Implement
    
    ```python
    class Solution(object):
        romanNumeralDict = {
            'I':1,
            'V':5,
            'X':10,
            'L':50,
            'C':100,
            'D':500,
            'M':1000
        }
        subtractionDict = {
            'IV':4,
            'IX':9,
            'XL':40,
            'XC':90,
            'CD':400,
            'CM':900
        }
        def romanToInt(self, s):
            """
            :type s: str
            :rtype: int
            """
            # 2. iterate the string and add the values
            result = 0
            index = 0
            while index < len(s):
                if index == len(s) - 1:
                    result += self.romanNumeralDict[s[index]]
                    break
                if self.isSubstraction(s[index],s[index+1]):
                    result += self.subtractionDict[s[index]+s[index+1]]
                    index +=2
                    continue
                result += self.romanNumeralDict[s[index]]
                index+=1
            return result
        
        def isSubstraction(self, char1, char2):
            if (char1+char2) in self.subtractionDict:
                return True
            return False
    ```
    

### Complexity

- Time complexity: O(n) iterate the character once
    
    ![Untitled](./Untitled.png)
    
- Space complexity: O(n)

### Problems & Improvement

- Do I need so many if ?
    
    ![Untitled](./Untitled%201.png)
    

# Improvement

### Thought Process

1. 
- Implement
    
    ```python
    
    ```
    

### Complexity

- Time complexity:
- Space complexity:

# Check special cases, check error

- 

# Note

- Impressive Solution in discussion
    - find the insight
        - only substract when the prev value is smaller than the current one
        - iterative backward
        
        ```python
        def romanToInt(self, s: str) -> int:
        	res, prev = 0, 0
        	dict = {'I':1, 'V':5, 'X':10, 'L':50, 'C':100, 'D':500, 'M':1000}
        	for i in s[::-1]:          # rev the s
        		if dict[i] >= prev:
        			res += dict[i]     # sum the value iff previous value same or more
        		else:
        			res -= dict[i]     # substract when value is like "IV" --> 5-1, "IX" --> 10 -1 etc 
        		prev = dict[i]
        	return res
        ```