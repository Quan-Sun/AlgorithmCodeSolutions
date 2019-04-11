Given two strings `A` and `B` of lowercase letters, return `true` if and only if we can swap two letters in `A` so that the result equals `B`.

Example:
```
Input: A = "ab", B = "ba"
Output: true
```

```
Input: A = "ab", B = "ab"
Output: false
```

```
Input: A = "aa", B = "aa"
Output: true
```

```
Input: A = "aaaaaaabc", B = "aaaaaaacb"
Output: true
```

```
Input: A = "", B = "aa"
Output: false
```

**NOTE**:
  - `0 <= A.length <= 20000`
  - `0 <= B.length <= 20000`
  - `A` and `B` consist only of lowercase letters.
  
***04/10/2019***

**solution 1**
```python
class Solution(object):
    def buddyStrings(self, A, B):
        """
        :type A: str
        :type B: str
        :rtype: bool
        """
        if len(A) != len(B) or set(A) != set(B): 
            return False       
        if A == B:
            return len(A) - len(set(A)) >= 1 # number of any a element is more than 1
        else:     
            index = []
            counter = 0
            for i in range(len(A)):
                if A[i] != B[i]:
                    counter += 1
                    index.append(i)       
                if counter > 2:
                    return False       
        return A[index[0]] == B[index[1]] and A[index[1]] == B[index[0]]
```
The time complexity is O(n).

**solution 2**
```python
class Solution(object):
    def buddyStrings(self, A, B):
        """
        :type A: str
        :type B: str
        :rtype: bool
        """
        if len(A) != len(B):
            return False
        if A == B:
            visited = set()
            for x in A:
                if x in visited:
                    return True
                visited.add(x)
            return False 
        else:
            pairs = []
            for x, y in itertools.izip(A, B):
                if x != y:
                    pairs.append((x, y))
                    if len(pairs) > 2:
                        return False
            return len(pairs) == 2 and pairs[0] == pairs[1][::-1]
```
The time complexity is O(n).
