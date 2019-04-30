Given a sorted array nums, remove the duplicates in-place such that each element appear only once and return the new length.

Do not allocate extra space for another array, you must do this by modifying the input array in-place with O(1) extra memory.

Example:

  Given nums = [1,1,2],

  Your function should return length = 2, with the first two elements of nums being 1 and 2 respectively.

  It doesn't matter what you leave beyond the returned length.
 
***02/27/2019*** 
```python
class Solution(object):
    def removeDuplicates(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        if len(nums) == 0:
            return None
        
        currNum = None
        currIndex = -1
        count = 0
        
        for num in nums:
            if num != currNum:
                index = currIndex + 1
                nums[index] = num
                currNum = num
                currIndex = index
                count += 1
                
        return count
```
The time complexity is O(n).
