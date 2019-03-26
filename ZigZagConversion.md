The string "PAYPALISHIRING" is written in a zigzag pattern on a given number of rows like this: (you may want to display this pattern in a fixed font for better legibility)

```
P   A   H   N
A P L S I I G
Y   I   R
```

And then read line by line: "PAHNAPLSIIGYIR"

Write the code that will take a string and make this conversion given a number of rows:
```
string convert(string s, int numRows);
```

Example:

```
Input: s = "PAYPALISHIRING", numRows = 3
Output: "PAHNAPLSIIGYIR"
```

```
Input: s = "PAYPALISHIRING", numRows = 4
Output: "PINALSIGYAHRPI"
Explanation:

P     I    N
A   L S  I G
Y A   H R
P     I
```

***03/26/2019***

```python
class Solution(object):
    def convert(self, s, numRows):
        """
        :type s: str
        :type numRows: int
        :rtype: str
        """
        if s is None:
            return
        if numRows == 1 or len(s) <= numRows:
            return s
        
        index, step = 0, 1
        stringList = [''] * numRows
        
        for x in s:
            stringList[index] += x
            if index == 0:
                step =  1            
            elif index == numRows - 1:
                step = -1
            index += step
        return ''.join(stringList)
```
The time complexity is O(n).
