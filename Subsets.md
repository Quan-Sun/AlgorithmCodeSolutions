Given a set of distinct integers, nums, return all possible subsets (the power set).

**NOTE**: The solution set must not contain duplicate subsets.

Example:
```
Input: nums = [1,2,3]
Output:
[
  [3],
  [1],
  [2],
  [1,2,3],
  [1,3],
  [2,3],
  [1,2],
  []
]
```

***04/04/2019***

**solution 1: DFS**
```python
class Solution:
    def subsets(self, nums):
        """
        :type nums: List[int]
        :rtype: List[List[int]]
        """
        ans=[]
        nums.sort()
        def dfs(index, path):
            ans.append(path)
            for i in range(index, len(nums)):
                dfs(i+1, path+[nums[i]])

        dfs(0,[])
        return ans
```
The time complexity is O(n).

**solution 2: iteration**
```python
class Solution(object):
    def subsets(self, nums):
        """
        :type nums: List[int]
        :rtype: List[List[int]]
        """
        ans = [[]]
        for num in sorted(nums):
            ans += [item+[num] for item in ans]
        return ans
```
The time complexity is O(nlogn).

**solution 3: Bit Manipulation**
```python
class Solution(object):
    def subsets(self, nums):
        """
        :type nums: List[int]
        :rtype: List[List[int]]
        """  
        ans = []
        nums.sort()
        for i in range(1<<len(nums)):
            tmp = []
            for j in range(len(nums)):
                if i & 1 << j:  # if i >> j & 1:
                    tmp.append(nums[j])
            ans.append(tmp)
        return ans
```
The time complexity is O(n<sup>2</sup>).
