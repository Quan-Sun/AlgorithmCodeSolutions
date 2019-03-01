mplement strStr().

Return the index of the first occurrence of needle in haystack, or -1 if needle is not part of haystack.

Example:
```
Input: haystack = "hello", needle = "ll"
Output: 2

Input: haystack = "aaaaa", needle = "bba"
Output: -1
```

***03/01/2019***
```python 
class Solution(object):
    def strStr(self, haystack, needle):
        """
        :type haystack: str
        :type needle: str
        :rtype: int
        """
        if haystack is None:
            return None
        try:
            return haystack.index(needle)
        except:
            return -1
```
The time complexity is O(n).
