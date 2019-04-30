Given an input string (s) and a pattern (p), implement regular expression matching with support for `'.'` and `'*'`.

```
'.' Matches any single character.
'*' Matches zero or more of the preceding element.
```

The matching should cover the entire input string (not partial).

Note:

 - s could be empty and contains only lowercase letters `a-z`.
 - p could be empty and contains only lowercase letters `a-z`, and characters like `.` or `*`.

Example:

```
Input:
s = "aa"
p = "a"
Output: false
Explanation: "a" does not match the entire string "aa".
```

```
Input:
s = "aa"
p = "a*"
Output: true
Explanation: '*' means zero or more of the precedeng element, 'a'. Therefore, by repeating 'a' once, it becomes "aa".
```

```
Input:
s = "ab"
p = ".*"
Output: true
Explanation: ".*" means "zero or more (*) of any character (.)".
```

```
Input:
s = "aab"
p = "c*a*b"
Output: true
Explanation: c can be repeated 0 times, a can be repeated 1 time. Therefore it matches "aab".
```

```
Input:
s = "mississippi"
p = "mis*is*p*."
Output: false
```

***03/27/2019***

```python
class Solution(object):
    def isMatch(self, s, p):
        """
        :type s: str
        :type p: str
        :rtype: bool
        """
        if s is None or p is None:
            return
        if len(s) == 0 or len(p) == 0:
            return
        
        import re
        p = '^' + p + '\Z'
        pattern = re.compile(p)
        
        return pattern.match(s)
```
The time complexity is O(n). (not sure)
