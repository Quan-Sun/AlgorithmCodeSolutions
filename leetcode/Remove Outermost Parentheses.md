A valid parentheses string is either empty `("")`, `"(" + A + ")"`, or `A + B`, where `A` and `B` are valid parentheses strings, and `+` represents string concatenation.  For example, `""`, `"()"`, `"(())()"`, and `"(()(()))"` are all valid parentheses strings.

A valid parentheses string `S` is primitive if it is nonempty, and there does not exist a way to split it into `S = A+B`, with `A` and `B` nonempty valid parentheses strings.

Given a valid parentheses string `S`, consider its primitive decomposition: `S = P_1 + P_2 + ... + P_k`, where `P_i` are primitive valid parentheses strings.

Return `S` after removing the outermost parentheses of every primitive string in the primitive decomposition of `S`.

Example:
```
Input: "(()())(())"
Output: "()()()"
Explanation: 
The input string is "(()())(())", with primitive decomposition "(()())" + "(())".
After removing outer parentheses of each part, this is "()()" + "()" = "()()()".
```

```
Input: "(()())(())(()(()))"
Output: "()()()()(())"
Explanation: 
The input string is "(()())(())(()(()))", with primitive decomposition "(()())" + "(())" + "(()(()))".
After removing outer parentheses of each part, this is "()()" + "()" + "()(())" = "()()()()(())".
```

```
Input: "()()"
Output: ""
Explanation: 
The input string is "()()", with primitive decomposition "()" + "()".
After removing outer parentheses of each part, this is "" + "" = "".
```

**Note**:

  - `S.length <= 10000`
  - `S[i]` is `"("` or `")"`
  - `S` is a valid parentheses string
  
***04/10/2019***

**solution 1: stack**
```python
class Solution(object):
    def removeOuterParentheses(self, S):
        """
        :type S: str
        :rtype: str
        """
        if S is None:
            return

        stack = []
        ans = []
        count = 0
        for par in S:
            if par == "(":
                count += 1
                stack.append(par)
            if par == ")":
                count -= 1
                stack.append(par)
            if count == 0:
                ans.append("".join(stack[1:-1]))
                stack = []
        return "".join(ans)
```
The time complexity is O(len(S)).

**solution 2**
```python
class Solution(object):
    def removeOuterParentheses(self, S):
        """
        :type S: str
        :rtype: str
        """
        start=0
        count=0
        result=""
        for i in range(0, len(S)):
            if S[i] == '(':
                count+=1
            else:
                count-=1
                if count==0:
                    result = result + S[start+1:i]
                    start=i+1
                    
        return result
```
The time complexity is O(len(S)).
