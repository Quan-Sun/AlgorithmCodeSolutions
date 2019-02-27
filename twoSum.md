Given an array of integers, return indices of the two numbers such that they add up to a specific target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

Example:
  Given nums = [2, 7, 11, 15], target = 9,

  Because nums[0] + nums[1] = 2 + 7 = 9,
  return [0, 1]
 
 ***02/27/2019***
```python
class Solution(object):
  def twoSum(self, nums, target):
      """
      :type nums: List[int]
      :type target: int
      :rtype: List[int]
      """
      storeList = [(target - num) for num in nums]

      if len(nums) == 0:
          return None

      for i,num in enumerate(storeList):
          for j,comp in enumerate(nums):
              if (comp == num) and (i != j):
                  return [i,j]
      return None
```
The time complexity is O(n<sup>2</sup>)

***02/27/2019 updated***
```python
class Solution(object):
    def twoSum(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """
        storeDict = {}
        
        if len(nums) == 0:
            return None
        for i, num in enumerate(nums):
            if target - num in storeDict:
                return [storeDict[target - num],i]
            
            storeDict[num] = i 
```
The time complexity is O(n)
