Given a non-empty array of integers, every element appears three times except for one, which appears exactly once. Find that single one.

**Note**:

Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?

Example:
```
Input: [2,2,3,2]
Output: 3
```

```
Input: [0,1,0,1,0,1,99]
Output: 99
```

***04/09/2019***

**solution 1**
```python
class Solution(object):
    def singleNumber(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        if not nums:
            return
        num_dict = {}
        for num in nums:
            num_dict[num] = num_dict.get(num, 0) + 1
        for k, v in num_dict.items():
            if v == 1:
                return k
        return
```
The time complexity is O(n).

**solution 2**
```python
class Solution(object):
    def singleNumber(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        if not nums:
            return
        return (3*sum(set(nums)) - sum(nums))//2
```
The time complexity is O(n).
