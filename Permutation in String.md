Given two strings s1 and s2, write a function to return true if s2 contains the permutation of s1. In other words, one of the first string's permutations is the substring of the second string.

Example:
```
Input:s1 = "ab" s2 = "eidbaooo"
Output:True
Explanation: s2 contains one permutation of s1 ("ba").
```

```
Input:s1= "ab" s2 = "eidboaoo"
Output: False
```

**NOTE**:
  - The input strings only contain lower case letters.
  - The length of both given strings is in range [1, 10,000].
  
  
***04/04/2019***

**HashTable/SlidingWindow**

```python
class Solution(object):
    def checkInclusion(self, s1, s2):
        """
        :type s1: str
        :type s2: str
        :rtype: bool
        """
        l = len(s1)
        n = len(s2)
        
        if not s1 or not s2 or l > n:
            return False
        
        vp = [0]*26
        vs = [0]*26
        
        for char in s1:
            vp[ord(char) - ord('a')] += 1
        
        i = 0
        while i < n:
            if i >= l:
                vs[ord(s2[i-l]) - ord('a')] -= 1
            vs[ord(s2[i]) - ord('a')] += 1
            
            if vs == vp:
                return True
            i += 1
            
        return False
```
The time complexity is O(n).

Similar with [Find All Anagrams in a String](https://github.com/Quan-Sun/AlgorithmCodeSolutions/blob/master/Find%20All%20Anagrams%20in%20a%20String.md)
