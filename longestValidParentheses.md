Given a string containing just the characters '(' and ')', find the length of the longest valid (well-formed) parentheses substring.

Example:
```
Input: "(()"
Output: 2
Explanation: The longest valid parentheses substring is "()"
```

```
Input: ")()())"
Output: 4
Explanation: The longest valid parentheses substring is "()()"
```

***03/02/2019 - Dynamic Programming***
```python
class Solution(object):
    def longestValidParentheses(self, s):
        """
        :type s: str
        :rtype: int
        """
        if s is None:
            return None
        
       # dp[i] records the longestValidParenthese EXACTLY ENDING at s[i]
        dp = [0 for x in xrange(len(s))]
        max_to_now = 0
        for i in range(1,len(s)):
            if s[i] == ')':
                # case 1: ()()
                if s[i-1] == '(':
                    # add nearest parentheses pairs + 2
                    dp[i] = dp[i-2] + 2
                # case 2: (()) 
                # i-dp[i-1]-1 is the index of last "(" not paired until this ")"
                elif i-dp[i-1]-1 >= 0 and s[i-dp[i-1]-1] == '(':
                    if dp[i-1] > 0: # content within current matching pair is valid 
                    # add nearest parentheses pairs + 2 + parentheses before last "("
                        dp[i] = dp[i-1] + 2 + dp[i-dp[i-1]-2]
                    else:
                    # otherwise is 0
                        dp[i] = 0
                max_to_now = max(max_to_now, dp[i])
        return max_to_now
```
The time complexity is O(n).

***03/02/2019 updated - Stack***
```python
class Solution(object):
    def longestValidParentheses(self, s):
        """
        :type s: str
        :rtype: int
        """
        if s is None:
            return None
        stack = [-1,]
        res = 0
        for idx, paren in enumerate(s):
            if paren == '(':
                stack.append(idx)
            else:
                stack.pop()
                if len(stack) == 0:
                    stack.append(idx)
                else:
                    res = max(res, idx - stack[-1])
        return res
```
The time complexity is O(n).

***03/02/2019 updated - Two Pass***
```python
class Solution(object):
    def longestValidParentheses(self, s):
        """
        :type s: str
        :rtype: int
        """
        if s is None:
            return None
            
        left, right = 0, 0
        res = 0
        for paren in s:
            if paren == '(':
                left += 1
            else:
                right += 1
            if left == right:
                res = max(res, left + right)
            if right > left:
                left = right = 0
        
        left = right = 0
        for i in range(len(s) - 1, -1, -1):
            if s[i] == '(':
                left += 1
            else:
                right += 1
            if left == right:
                res = max(res, left + right)
            if left > right:
                left = right = 0
        return res
```
The time complexity is O(n).
