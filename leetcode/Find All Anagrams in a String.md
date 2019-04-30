Given a string s and a non-empty string p, find all the start indices of p's anagrams in s.

Strings consists of lowercase English letters only and the length of both strings s and p will not be larger than 20,100.

The order of output does not matter.

Example;
```
Input:
s: "cbaebabacd" p: "abc"

Output:
[0, 6]

Explanation:
The substring with start index = 0 is "cba", which is an anagram of "abc".
The substring with start index = 6 is "bac", which is an anagram of "abc".
```

```
Input:
s: "abab" p: "ab"

Output:
[0, 1, 2]

Explanation:
The substring with start index = 0 is "ab", which is an anagram of "ab".
The substring with start index = 1 is "ba", which is an anagram of "ab".
The substring with start index = 2 is "ab", which is an anagram of "ab".
```

***04/04/2019***

**HashTable/SlidingWindow**

**Idea**: Setting two hash table, respectively counting s and p; setting a sliding window, count of the prev char minus 1 when silding the window
```python
class Solution(object):
    def findAnagrams(self, s, p):
        """
        :type s: str
        :type p: str
        :rtype: List[int]
        """
        n = len(s)
        l = len(p)
        
        if not p or l > n:
            return []
            
        ans = []
        vp = [0]*26
        vs = [0]*26
        
        for char in p:
            vp[ord(char) - ord('a')] += 1
        
        i = 0
        while i < n:
            if i >= l:
                vs[ord(s[i-l]) - ord('a')] -= 1
            vs[ord(s[i]) - ord('a')] += 1
            if vp == vs:
                ans.append(i+1-l)
            i += 1
        return ans
```

The time complexity is O(n).
