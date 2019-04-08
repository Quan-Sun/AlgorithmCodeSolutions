Given an array with `n` integers, your task is to check if it could become non-decreasing by modifying at most `1` element.

We define an array is non-decreasing if `array[i] <= array[i + 1]` holds for every i (1 <= i < n).

Example:
```
Input: [4,2,3]
Output: True
Explanation: You could modify the first 4 to 1 to get a non-decreasing array.
```

```
Input: [4,2,1]
Output: False
Explanation: You can't get a non-decreasing array by modify at most one element.
```

**Note**: The `n` belongs to [1, 10,000].

***04/08/2019***

**Idea**: Counting the number of decreasing situation in the array; if count is 0, return True; if count is greater than 1, return False; if count is 1, we should discuss with different situations, and the key is we can change the index number(nums[index-1]<=nums[index+1]) and index+1 number(nums[index]<=nums[index+2]).

**solution 1**
```python
class Solution(object):
    def checkPossibility(self, nums):
        """
        :type nums: List[int]
        :rtype: bool
        """
        p = None
        for i in range(len(nums) - 1):
            if nums[i] > nums[i+1]:
                if p is not None:
                    return False
                p = i

        return (p is None or p == 0 or p == len(nums)-2 or
                nums[p-1] <= nums[p+1] or nums[p] <= nums[p+2])
```
The time complexity is O(n).

**solution 2**
```python
class Solution(object):
    def checkPossibility(self, nums):
        """
        :type nums: List[int]
        :rtype: bool
        """
        if not nums:
            return
        
        count = 0
        index = 0
        n = len(nums)
        for i in range(n-1):
            if nums[i] > nums[i+1]:
                count += 1
                index = i
        if count > 1:
            return False
        
        if count == 0:
            return True
        
        if count == 1:
            if n <= 2:
                return True
            if index == 0:
                return True
            if index == n-2:
                return True               
            if index + 1 <= n-1:
                if nums[index-1] <= nums[index+1]:
                    return True
            if index + 2 <= n-1:
                if nums[index] <= nums[index+2]:
                    return True
            return False
```
The time complexity is O(n).
