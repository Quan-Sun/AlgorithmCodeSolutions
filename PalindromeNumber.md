Determine whether an integer is a palindrome. An integer is a palindrome when it reads the same backward as forward.

Example:

```
Input: 121
Output: true
```

```
Input: -121
Output: false
Explanation: From left to right, it reads -121. From right to left, it becomes 121-. Therefore it is not a palindrome.
```

```
Input: 10
Output: false
Explanation: Reads 01 from right to left. Therefore it is not a palindrome.
```

***03/27/2019***

```python
class Solution(object):
    def isPalindrome(self, x):
        """
        :type x: int
        :rtype: bool
        """
        if type(x) != int or x is None:
            return 
        
        if x < 0:
            return False
        
        x = str(x)
        n = len(x) // 2
        
        if len(x) == 0:
            return
        
        if len(x) % 2 == 1:
            return self.check(x, n, n)
        
        return self.check(x, n-1, n)
        
    def check(self, s, i, j):
        while i >= 0 and j <= len(s):
            if s[i] != s[j]:
                return False
            i = i - 1
            j = j + 1
        return True
```
The time complexity is O(logn).
