Given a non-empty array of integers, every element appears twice except for one. Find that single one.

**Note**:

Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?

Example:
```
Input: [2,2,1]
Output: 1
```

```
Input: [4,1,2,1,2]
Output: 4
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

**solution 2: bitwise operation**
```python
class Solution(object):
    def singleNumber(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        ans=0
        for num in nums:
            ans^=num #bitwise exclusive or
        return ans
```
The time complexity is O(n).
