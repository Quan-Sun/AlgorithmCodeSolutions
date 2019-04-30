All DNA is composed of a series of nucleotides abbreviated as A, C, G, and T, for example: "ACGAATTCCG". When studying DNA, it is sometimes useful to identify repeated sequences within the DNA.

Write a function to find all the 10-letter-long sequences (substrings) that occur more than once in a DNA molecule.

Example:
```
Input: s = "AAAAACCCCCAAAAACCCCCCAAAAAGGGTTT"

Output: ["AAAAACCCCC", "CCCCCAAAAA"]
```

***04/09/2019***

**solution 1**
```python
class Solution(object):
    def findRepeatedDnaSequences(self, s):
        """
        :type s: str
        :rtype: List[str]
        """
        if not s:
            return
        seq_dict = {}
        ans = []
        n = len(s)
        for i in range(n-9):
            seq_dict[s[i:i+10]] = seq_dict.get(s[i:i+10], 0) + 1
        for k, v in seq_dict.items():
            if v > 1:
                ans.append(k)
        return ans
```
The time complexity is O(n).

**solution 2**
```python
class Solution(object):
    def findRepeatedDnaSequences(self, s):
        """
        :type s: str
        :rtype: List[str]
        """
        if not s:
            return
        seen = set()
        ans = set()
        n = len(s)
        for i in range(n-9):
            cur = s[i:i + 10]
            if cur in seen:
                ans.add(cur)
            else:
                seen.add(cur)
        return list(ans)
```
The time complexity is O(n).
