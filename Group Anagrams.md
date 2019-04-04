Given an array of strings, group anagrams together.

Example:
```
Input: ["eat", "tea", "tan", "ate", "nat", "bat"],
Output:
[
  ["ate","eat","tea"],
  ["nat","tan"],
  ["bat"]
]
```

**NOTE**:
  - All inputs will be in lowercase.
  - The order of your output does not matter.
  
***04/04/2019***

**HashTable**

```python
class Solution(object):
    def groupAnagrams(self, strs):
        """
        :type strs: List[str]
        :rtype: List[List[str]]
        """
        ans = {}
        for s in sorted(strs):
            key = tuple(sorted(s))
            ans[key] = ans.get(key, []) + [s]
        return ans.values()
```
The time complexity is O(n).


```python
class Solution(object):
    def groupAnagrams(self, strs):
        """
        :type strs: List[str]
        :rtype: List[List[str]]
        """
        ans = {}
        
        for s in strs:
            key = ''.join(sorted(s))
            ans[key] = ans.get(key, []) + [s]
        return ans.values()
```
The time complexity is O(n).
