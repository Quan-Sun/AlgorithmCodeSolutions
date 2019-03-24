Given a string s, find the longest palindromic substring in s. You may assume that the maximum length of s is 1000.

Example:
```
Input: "babad"
Output: "bab"
Note: "aba" is also a valid answer.
```

```
Input: "cbbd"
Output: "bb"
```

***03/24/2019***

```python
class Solution(object):
    def longestPalindrome(self, s):
        """
        :type s: str
        :rtype: str
        """
        if s is None or len(s) == 0:
            return
        
        lp = ""
        for i in range(len(s)):
            sub = self.find(s, i, i)
            if len(sub) > len(lp):
                lp = sub
            
            sub = self.find(s, i, i+1)
            if len(sub) > len(lp):
                lp = sub
        return lp
    
    def find(self, s, i, j):
        while i >= 0 and j < len(s) and s[i] == s[j]:
            i -= 1
            j += 1
        return s[i+1:j]
```
The time complexity is O(n).
