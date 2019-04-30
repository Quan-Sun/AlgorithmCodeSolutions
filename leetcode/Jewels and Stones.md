You're given strings `J` representing the types of stones that are jewels, and `S` representing the stones you have.  Each character in `S` is a type of stone you have.  You want to know how many of the stones you have are also jewels.

The letters in `J` are guaranteed distinct, and all characters in `J` and `S` are letters. Letters are case sensitive, so `"a"` is considered a different type of stone from `"A"`.

Example:
```
Input: J = "aA", S = "aAAbbbb"
Output: 3
```

```
Input: J = "z", S = "ZZ"
Output: 0
```

**NOTE**:
  - `S` and `J` will consist of letters and have length at most 50.
  - The characters in `J` are distinct.
  
***04/10/2019***

**solution 1**
```python
class Solution(object):
    def numJewelsInStones(self, J, S):
        """
        :type J: str
        :type S: str
        :rtype: int
        """
        if J is None or S is None:
            return
        stone_dict = {}
        for s in S:
            if s in J:
                stone_dict[s] = stone_dict.get(s, 0) + 1
            
        return sum([v for v in stone_dict.values()])
```
The time complexity is O(len(S)).

**solution 2**
```python
class Solution(object):
    def numJewelsInStones(self, J, S):
        """
        :type J: str
        :type S: str
        :rtype: int
        """
        count = 0
        for s in S:
            if s in  J:
                count +=  1
        return count
```
The time complexity is O(len(S)).

**solution 3**
```python
class Solution(object):
    def numJewelsInStones(self, J, S):
        """
        :type J: str
        :type S: str
        :rtype: int
        """
        return len([s for s in S if s in J]) # sum(s in J for s in S)
```
The time complexity is O(len(S)).
