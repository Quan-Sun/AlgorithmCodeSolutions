Given a string, find the length of the longest substring without repeating characters.

Example:
```
Input: "abcabcbb"
Output: 3 
Explanation: The answer is "abc", with the length of 3. 
```

```
Input: "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.
```

```
Input: "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3. 
             Note that the answer must be a substring, "pwke" is a subsequence and not a substring.
```

***03/24/2019***

```python
class Solution(object):
        
    def lengthOfLongestSubstring(self, s):
        """
        :type s: str
        :rtype: int
        """
        if s is None or len(s) == 0:
            return
        
        n = len(s)
        usedChar = {}
        start = maxlen = 0
        
        for i in range(n):
            if s[i] in usedChar and start <= usedChar[s[i]]:
                start = usedChar[s[i]] + 1
            else:
                maxlen = max(maxlen, i - start + 1)
            usedChar[s[i]] = i
        return maxlen
```
The time complexity is O(n).
