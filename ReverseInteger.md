Given a 32-bit signed integer, reverse digits of an integer.

Example:

```
Input: 123
Output: 321
```

```
Input: -123
Output: -321
```

```
Input: 120
Output: 21
```

**Note**:
Assume we are dealing with an environment which could only store integers within the 32-bit signed integer range: [−231,  231 − 1]. For the purpose of this problem, assume that your function returns 0 when the reversed integer overflows.

***03/27/2019***

```python
class Solution(object):
    def reverse(self, x):
        """
        :type x: int
        :rtype: int
        """
        if x >= 0:
            result = self.get_result(x)
        else:
            x = -x
            result = -self.get_result(x)
            
        if 2**31-1 >= result >= -2**31:
            return result
        else:
            return 0
        
    def get_result(self, x):
        get_list = list(str(x))
        result = int(''.join(get_list[::-1]))
        return result
```
The time complexity is O(n).
