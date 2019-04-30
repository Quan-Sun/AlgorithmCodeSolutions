Implement atoi which converts a string to an integer.

The function first discards as many whitespace characters as necessary until the first non-whitespace character is found. Then, starting from this character, takes an optional initial plus or minus sign followed by as many numerical digits as possible, and interprets them as a numerical value.

The string can contain additional characters after those that form the integral number, which are ignored and have no effect on the behavior of this function.

If the first sequence of non-whitespace characters in str is not a valid integral number, or if no such sequence exists because either str is empty or it contains only whitespace characters, no conversion is performed.

If no valid conversion could be performed, a zero value is returned.

**Note**:

Only the space character ' ' is considered as whitespace character.
Assume we are dealing with an environment which could only store integers within the 32-bit signed integer range: [−−2<sup>31</sup>,2<sup>31</sup> − 1]. If the numerical value is out of the range of representable values, INT_MAX (2<sup>31</sup> − 1) or INT_MIN (−2<sup>31</sup>) is returned.

Example:

```
Input: "42"
Output: 42
```

```
Input: "   -42"
Output: -42
Explanation: The first non-whitespace character is '-', which is the minus sign.
             Then take as many numerical digits as possible, which gets 42.
```

```
Input: "4193 with words"
Output: 4193
Explanation: Conversion stops at digit '3' as the next character is not a numerical digit.
```

```
Input: "words and 987"
Output: 0
Explanation: The first non-whitespace character is 'w', which is not a numerical 
             digit or a +/- sign. Therefore no valid conversion could be performed.
```

```
Input: "-91283472332"
Output: -2147483648
Explanation: The number "-91283472332" is out of the range of a 32-bit signed integer.
             Thefore INT_MIN (−231) is returned.
```

***03/27/2019***

**Better solution is to be continued**

```python
class Solution(object):
    def myAtoi(self, str):
        """
        :type str: str
        :rtype: int
        """
        INT_MAX = 2147483647
        INT_MIN = -2147483648
        
        str = str.lstrip()
        if str == "" or None:
            return 0
        
        num_list = ['0', '1', '2', '3', '4', '5', '6', '7', '8', '9']
        trans_to_list = list(str)
        result = []
        
        
        if trans_to_list[0] == '-':
            for char in trans_to_list[1:]:
                if char in num_list:
                    result.append(char)
                else:
                    break
                    
            if len(result) == 0:
                return 0
            
            result = int('-' + ''.join(result))
            if result >= INT_MIN:
                return result
            else:
                return INT_MIN
        
        elif trans_to_list[0] == '+':
            for char in trans_to_list[1:]:
                if char in num_list:
                    result.append(char)
                else:
                    break
                    
            if len(result) == 0:
                return 0
            
            result = int(''.join(result))
            if result <= INT_MAX:
                return result
            else:
                return INT_MAX
            
        elif trans_to_list[0] in num_list:
            for char in trans_to_list:
                if char in num_list:
                    result.append(char)
                else:
                    break
                    
            if len(result) == 0:
                return 0
            
            result = int(''.join(result))
            if result <= INT_MAX:
                return result
            else:
                return INT_MAX
        
        else:
            return 0
```        
The time complexity is O(n).       
