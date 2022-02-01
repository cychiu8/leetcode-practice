# 0844. Backspace String Compare

* Difficulty: easy
* Link: https://leetcode.com/problems/backspace-string-compare/
* Topics: Array-String

# Clarification

1. Check the inputs and outputs
    - INPUT: two string
    - OUTPUT: boolean

# Naive Solution

### Thought Process

1. 每個 string 皆從最後面開始往回看
2. 若為 # 紀錄若遇到文字要往回走一格
3. 比對兩個 string 當下在的文字是否一樣
- Implement
    
    ```python
    class Solution:
        def backspaceCompare(self, s: str, t: str) -> bool:
            sIdx = len(s)-1
            tIdx = len(t)-1
            sSkip = 0
            tSkip = 0
            while sIdx >=0 or tIdx >=0:
                while sIdx >=0:
                    if s[sIdx] == '#':
                        sSkip += 1
                        sIdx -= 1
                    elif sSkip > 0:
                        sSkip -= 1
                        sIdx -= 1
                    else:
                        break
                while tIdx >=0:
                    if t[tIdx] == '#':
                        tSkip += 1
                        tIdx -= 1
                    elif tSkip > 0:
                        tSkip -= 1
                        tIdx -= 1
                    else:
                        break
                if sIdx >= 0 and tIdx >= 0 and s[sIdx] != t[tIdx]:
                    return False
                if (sIdx >=0 ) != (tIdx >=0):
                    return False
                sIdx -= 1
                tIdx -= 1
            return True
    ```
    

### Complexity

- Time complexity: $O(n)$
- Space complexity:$O(1)$