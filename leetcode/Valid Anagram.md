Given two strings s and t , write a function to determine if t is an anagram of s.

Example:
```
Input: s = "anagram", t = "nagaram"
Output: true
```

```
Input: s = "rat", t = "car"
Output: false
```

**NOTE**:
  - You may assume the string contains only lowercase alphabets.
  
***04/04/2019***
```python
class Solution(object):
    def isAnagram(self, s, t):
        """
        :type s: str
        :type t: str
        :rtype: bool
        """
        
        vs = {}
        vp = {}
        
        if len(s) != len(t):
            return False
        
        for char in t:
            vp[char] = vp.get(char, 0) + 1
        
        for char in s:
            vs[char] = vs.get(char, 0) + 1
        
        if vp == vs:
            return True
        return False
```
The time complexity is O(n).



```python
class Solution(object):
    def isAnagram(self, s, t):
        """
        :type s: str
        :type t: str
        :rtype: bool
        """
        if len(s) != len(t):
            return False

        for i in range(ord('a'), ord('z')+1):
            c = chr(i)
            if s.count(c) != t.count(c):
                return False

        return True
```
The time complexity is O(n).
