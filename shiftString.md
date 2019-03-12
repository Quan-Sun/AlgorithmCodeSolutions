Given an string，moving specific n chars to end of the string.
The time complexity should be O(n), and space complexity should be O(1).

Example:
```
string = 'abcdef'
n = 2
output = 'cdefab'
```

***03/11/2019***                
**Brute-force**
```python
class Solution(object):
    def shiftString(self, s, n):
        """
        :type s: str
        :type n: int
        :rtype: str
        """
        if n < 0:
          return None
          
        while n > 0:
          for j in range(len(s)):
            s[i-1], s[i] = s[i], s[i-1]
          n -= 1
        return s
```
The time complexity is O(m*n).

***03/11/2019***                
**Three steps change**
```python
class Solution(object):
    def shiftString(self, s, n):
        """
        :type s: str
        :type n: int
        :rtype: str
        """
        if n < 0:
          return None
        
        # Split string into two parts X and Y
        s[0: n] = s[0: n][::-1]  # inverse X
        s[n:] = s[n:][::-1] # inverse Y
        return s[:][::-1] # inverse whole string
```
The time complexity is O(n).
