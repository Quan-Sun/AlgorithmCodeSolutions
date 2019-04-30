***03/19/2019***

```python 
class UnionFindSet:
    def __init__(self, n):
        self._parnets = [i for i in range(n+1)]
        self.ranks = [1 for _ in range(n+1)]
        
    def find(self, u):
        initial = u
        while u != self._parents[u]:  //find the root
            u = self._parents[u]
        self._parents[initial] = u //compression
        return u
        
    def union(self, u, v): //union two components by ranks
        pu, pv = find(u), find(v)
        if pu == pv: 
            return False
        if self._ranks[pu] < self._ranks[pv]:
            self._parents[pu] = pv
        elif self._ranks[pu] > self._ranks[pv]:
            self._parents[pv] = pu
        else:
            self._parents[pu] = pv
            self._ranks[pv] += 1
        return True
```

Know more about Disjoint-Set, seeing: [1](https://www.youtube.com/watch?v=VJnUwsE4fWA&index=16&list=PLLuMmzMTgVK5Hy1qcWYZcd7wVQQ1v0AjX&t=0s) ; [2](https://www.cs.princeton.edu/courses/archive/spring13/cos423/lectures/UnionFind.pdf)
