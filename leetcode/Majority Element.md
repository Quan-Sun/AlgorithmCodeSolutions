Given an array of size n, find the majority element. The majority element is the element that appears more than `n/2` times.

You may assume that the array is non-empty and the majority element always exist in the array.

Example:
```
Input: [3,2,3]
Output: 3
```

```
Input: [2,2,1,1,1,2,2]
Output: 2
```

***04/09/2019***

**solution 1**
```python
class Solution(object):
    def majorityElement(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        if not nums:
            return 
        num_dict = {}
        for num in nums:
            num_dict[num] = num_dict.get(num, 0) + 1
        n = len(nums)//2
        for k, v in num_dict.items():
            if v > n:
                return k
        return 
```
The time complexity is O(n).

**solution 2**
```python
class Solution(object):
    def majorityElement(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        if not nums:
            return
        nums = sorted(nums, reverse = True)
        index = len(nums)//2
        return nums[index]
```
The time complexity is O(nlogn).
