Given a string S, we can transform every letter individually to be lowercase or uppercase to create another string.  Return a list of all possible strings we could create.

Example:
```
Input: S = "a1b2"
Output: ["a1b2", "a1B2", "A1b2", "A1B2"]

Input: S = "3z4"
Output: ["3z4", "3Z4"]

Input: S = "12345"
Output: ["12345"]
```

***04/04/2019***

**solution1: DFS**
```python
class Solution(object):
    def letterCasePermutation(self, S):
        """
        :type S: str
        :rtype: List[str]
        """
        ans = []
        
        def dfs(S, i, n):
            if i == n:
                ans.append(''.join(S))
                return
            dfs(S, i+1, n)
            if not S[i].isalpha(): return
            S[i] = chr(ord(S[i]) ^ (1 << 5))
            dfs(S, i+1, n)
            S[i] = chr(ord(S[i]) ^ (1 << 5))
            
        dfs(list(S), 0, len(S))
        return ans
```
The time complexity is O(n*2<sup>m</sup>).  ps: m is number of letters in the string

**solution 2**
```python
class Solution(object):        
    def letterCasePermutation(self, S):
            ans = ['']
            for char in S:
                if char.isalpha():
                    ans = [i+j for i in ans for j in [char.upper(), char.lower()]]
                else:
                    ans = [i+char for i in ans]
            return ans
```
The time complexity is O(n).

**solution 3**
```python
class Solution(object):
    def letterCasePermutation(self, S):
        """
        :type S: str
        :rtype: List[str]
        """
        ans = [S]
        for i, char in enumerate(S):
            if char.isalpha():
                ans.extend([s[:i] + s[i].swapcase() + s[i+1:] for s in ans])
        return asn
```
The time complexity is O(n).
